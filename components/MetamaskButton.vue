<script setup>
import Web3 from 'web3'
import { onMounted } from 'vue'
import { Buffer } from 'buffer'

const metamaskInstalled = useState('MM_installed', ()=>false);
const connected = useState('MM_connected', ()=>false);
const correctNetwork = useState('MM_correctNetwork');
const metamaskReady = useState('MM_ready', ()=>false);
const metamaskAddress = useState('MM_address');
const attemptingConnect = useState(()=>false);
const signedMessage = useState(()=>false);

function checkMetamaskInstalled() {
  const {ethereum} = window;
  return Boolean(ethereum && ethereum.isMetaMask);
}

async function connectMetamask(requestAccount){
  attemptingConnect.value = true;
  const ethereum = window.ethereum;
  try {
    const web3 = new Web3(window.ethereum)
    if (requestAccount){
      await ethereum.request({ method: 'eth_requestAccounts' })
    }
    var accounts = await web3.eth.getAccounts()
    console.log(accounts);

    if (accounts.length < 1){
      throw "No accounts connected"
    }
    connected.value=true;
    metamaskAddress.value = accounts[0]
    console.log("SETTING", metamaskAddress.value); 
    let chainId = await web3.eth.net.getId();

    // TODO make correct chainID environment variable
    correctNetwork.value = ( chainId== 80001)
    if (correctNetwork){
      metamaskReady.value = true
    }

  } catch (error) {
    // User denied account access
    if (requestAccount){
      console.error('Metamask denied request', error);
    }
  } 
  attemptingConnect.value = false;
}

onMounted(()=>{
  metamaskInstalled.value = checkMetamaskInstalled()
  if (metamaskInstalled){
    connectMetamask(false);
  }
});

async function web3RequestUserSign(){
  var dataToSign="1593352322389725186" // correct*/
  /*var dataToSign="1496496288757473280" // wrong*/
  try {
    const ethereum = window.ethereum;
    const from = metamaskAddress.value;

    const msg = `0x${Buffer.from(dataToSign, 'utf8').toString('hex')}`;
    const sign = await ethereum.request(
      { method: 'personal_sign',
      params: [msg, from, 'Example password']
      }
    );
    signedMessage.value = sign;
  } catch (err) {
    console.log('sign failed', err)
  }
}

function openChromestall(){
  window.open("https://metamask.io/", '_blank');
}

</script>
<template>
  <div class="h-full">
    <button v-if="!metamaskInstalled" class="button installstate" @click="openChromestall">
      <div class="buttontext">
        Install MetaMask
      </div>
    </button>

    <button @click="connectMetamask(true)" v-else-if="!connected && !attemptingConnect" class="button connectstate">
      <div class="buttontext">
        Connect Wallet
      </div>
    </button>
    <button v-else-if="attemptingConnect" class="button loadingstate">
      <div class="buttontext">
        Connecting..
      </div>
    </button>
    <div v-else-if="connected" class="button connectedstate">
      {{metamaskAddress.slice(0,9)}}...{{metamaskAddress.slice(35)}}
    </div>
  </div>
</template>

<style scoped>
.button{
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 3px 16px;
  gap: 10px;

  width: 200px;
  height: 100%;

  border-radius: 6px;
}

.buttontext{
  width: 100%;
  height: 20px;

  /*font-family: 'Inter';*/
  font-style: normal;
  font-weight: 700;
  font-size: 16px;
  line-height: 20px;
  /* identical to box height */

  text-align: center;
}

.connectstate{
  background: #F36DFF;
  color: #FFFFFF;
}

.loadingstate{
  background: #4A3E4B;
  color: white;
}
.installstate{
  background: #C2C2C2;
  color: black;
}
.connectedstate{
  background: #FFFFFF;
  border: 2px solid #00FF0A;
  border-radius: 6px;
}
</style>

