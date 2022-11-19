<script setup>
const connected=useState("MM_connected")
const twitterId = useState("twitter_id", ()=>null);
const twitterName = useState("twitter_name",()=>null);
const twitterIdSigned = useState("twitter_id_signed", ()=>null);
const signbuttonloading = useState(()=>false);
const metamaskAddress = useState('MM_address', ()=>false);
import { Buffer } from 'buffer'

async function web3RequestUserSign(){
  signbuttonloading.value = true;
  var dataToSign= String(twitterId.value);
  console.log(dataToSign);
  try {
    const ethereum = window.ethereum;
    const from = metamaskAddress.value;

    const msg = `0x${Buffer.from(dataToSign, 'utf8').toString('hex')}`;
    const sign = await ethereum.request(
      { method: 'personal_sign',
      params: [msg, from, 'Example password']
      }
    );
    twitterIdSigned.value = sign;
    console.log(sign)
  } catch (err) {
    console.log('sign failed', err)
  } finally {
    signbuttonloading.value = false
  }
}

</script>


<template>

  <instruction-card> 
    <div class="cont">
      <div class="textcontainer">Hello {{twitterName}} !! <br>If this is you, go ahead and sign your twitter id {{twitterId}}
      </div>
    </div>

    <div class="cont justify-end">
      <div v-if="!signbuttonloading">
        <button class="nextbutton" @click="web3RequestUserSign()">
          <div>Sign Message</div>
        </button>
      </div>
      <div v-else>
        <button class="nextbutton loadingstate">
          <div>Loading</div>
        </button>
      </div>
    </div>
  </instruction-card> 
</template>

<style scoped>
.cont{
  /* Auto layout */

  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 12px;
  gap: 10px;

  /*width: 543px;*/
  /*height: 39px;*/


  /* Inside auto layout */

  flex: none;
  align-self: stretch;
  flex-grow: 0;
}
.textcontainer{

  /*font-family: 'Inter';*/
  /*font-style: normal;*/
  font-weight: 400;
  font-size: 16px;
  /*line-height: 15px;*/
  /*[> identical to box height <]*/


  color: #000000;


  /* Inside auto layout */

  flex: none;
  flex-grow: 0;
}
.nextbutton{

  /* Auto layout */

  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 3px 16px;
  gap: 10px;

  width: 120px;
  height: 32px;

  background: #2797FF;
  border-radius: 6px;

  /* Inside auto layout */

  flex: none;
  order: 0;
  flex-grow: 0;
  color: #FFFFFF;
  font-size: 14px;
}

.loadingstate{
  background: #4A3E4B;
  color: white;
  font-size: 14px
}

</style>
