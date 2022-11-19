<template>
 <div class="box"> 
  <div class="titlebox">
    <div class="titletext">
      {{ param }}
    </div>
  </div>
  <div class="valuebox">
    <div class="valuetext">
      {{ paramval }}
    </div>
  </div>
 </div>
</template>

<script setup>
const props = defineProps(['param', 'paramval'])
</script>

<style scoped>
.box{
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
  width: 93px;
  height: 76px;
  background: #FFFFFF;
  flex: none;
  flex-grow: 0;
}
.titlebox{
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 0px;
  gap: 10px;
  width: 65px;
  height: 15px;
}
.titletext{
  width: 65px;
  height: 15px;
  font-style: normal;
  font-weight: 700;
  font-size: 12px;
  line-height: 15px;
  text-align: center;
  color: #000000;
}
.valuebox{
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 0px;
  gap: 10px;
  width: 38px;
  height: 36px;
  flex: none;
  flex-grow: 0;
}
.valuetext{
  width: 38px;
  height: 36px;
  font-style: normal;
  font-weight: 400;
  font-size: 30px;
  line-height: 36px;
  text-align: center;
  color: #000000;
  /* Inside auto layout */
  flex: none;
  flex-grow: 0;
}
</style>
