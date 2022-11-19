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

/*watch(metamaskReady, (value)=>{*/
    /*if (value){*/
      /*time.sleep(3);*/
      /*web3RequestUserSign("All I want for christmas is coins")*/
    /*}*/
  /*}*/
/*);*/

</script>

<template>
  <div class="container mx-auto">
    <div v-if="!metamaskInstalled">
     Please install metamask 
    </div>
    <div v-else>
      <div v-if="connected">
        HI {{metamaskAddress}} <br>You are connected
        
        <div v-if="!correctNetwork">BUT connected to the wrong network and refresh<br>Please connect to MUMBAI Polygon</div>
        <div v-else>
          <div v-if="!signedMessage" >
            <button @click="web3RequestUserSign()">Click here to sign a message</button>
          </div>
          <div v-else>
            Please post this on your wall --<br>@fortheglyph register {{metamaskAddress}} {{signedMessage}}<br>to register
          </div>
        </div>
      </div>
      <div v-else>
        <button v-if="!attemptingConnect" @click="connectMetamask(true)">Click to connect</button>
        <div v-else>Attempting to connect</div>
      </div>
    </div>
  </div>
</template>
