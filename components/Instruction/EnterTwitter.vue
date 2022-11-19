<script setup>
const connected = useState("MM_connected");
const nextbuttonloading = useState(()=>{return false});
const twitterHandle = useState(()=>{return ""});
const twitterId = useState("twitter_id", ()=>null);
const twitterName = useState("twitter_name",()=>null);

async function nextclick(){
  console.log(nextbuttonloading.value)
  nextbuttonloading.value=!nextbuttonloading.value
  try{
    const value = twitterHandle.value.slice(1)
    const data = await $fetch(`http://143.198.221.207:3000/twitter/userlookup?handle=${value}`);
    console.log(data)
    twitterId.value = data.id;
    twitterName.value = data.name;
  }
  catch (err){
    console.log(err)
    alert(`Unable to get information for ${twitterHandle.value}, check handle or try again later`)
  }
  finally{
    nextbuttonloading.value = false
  }
}

</script>

<template>
  <instruction-card> 
    <div class="cont">
      <div class="textcontainer">Enter your twitter handle</div>
    </div>
    <div class="cont">
      <input class="inputcontainer" v-model="twitterHandle" placeholder="@elonmusk"/>
    </div>
    <div class="cont justify-end">
      <div v-if="!nextbuttonloading">
        <button class="nextbutton" @click="nextclick()">
          <div>Next</div>
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
.inputcontainer{
  box-sizing: border-box;

  /* Auto layout */
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 8px 16px;
  gap: 8px;
  margin: 0 20px;

  width: 100%;
  height: 36px;

  background: #FFFFFF;
  border: 1px solid #E0E0E0;
  border-radius: 2px;
}

.nextbutton{

  /* Auto layout */

  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 3px 16px;
  gap: 10px;

  width: 88px;
  height: 32px;

  background: #2797FF;
  border-radius: 6px;

  /* Inside auto layout */

  flex: none;
  order: 0;
  flex-grow: 0;

    flex: none;
    order: 0;
    flex-grow: 0;
    color: #FFFFFF;
}

.loadingstate{
  background: #4A3E4B;
  color: white;
}
</style>
