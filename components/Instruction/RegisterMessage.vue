<template>
  <instruction-card>
    <div class="cont">
      <div class="textcontainer">
        You are finally there! Tweet this to register
      </div>
    </div>
    <div class="cont pl-7 bg-slate-300 mx-6 my-3 rounded">
      <div class="textcontainer longtextcontainer max-w-full my-0">
        @fortheglyph {{registerMessage}}
      </div>
    </div>
    <div class="">
    </div>


    <div class="cont justify-end">
      <div v-if="!copied">
        <button class="copybutton" @click="copyText()">
          <div>Click to copy</div>
        </button>
      </div>
      <div v-else>
        <button class="copybutton copystate">
          <div>Copied</div>
        </button>
      </div>
    </div>
 
  </instruction-card>
  
</template>

<script setup>
const metamaskAddress = useState('MM_address', ()=>false);
const twitterIdSigned = useState("twitter_id_signed", ()=>null);
const copied = useState(()=>false);

const registerMessage = computed(()=>{
  return `register ${metamaskAddress.value} ${twitterIdSigned.value}`
});

function copyText(){
  const text = `@fortheglyph register ${metamaskAddress.value} ${twitterIdSigned.value}`
  navigator.clipboard.writeText(text);
  copied.value=true
}
</script>

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

.longtextcontainer{
  display: inline-block;
  overflow-wrap: break-word;
  font-size: 14px;
}


.copybutton{

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

.copystate{
  background: #4A3E4B;
  color: white;
  font-size: 14px
}

</style>
