<script setup>
const connected=useState("MM_connected")
const twitterId = useState("twitter_id", ()=>null);
const twitterName = useState("twitter_name",()=>null);
const twitterIdSigned = useState("twitter_id_signed",()=>null);

</script>

<template>
  <div class="page h-screen"> 
    <div class="spacing"/>

    <user-score/>
    <div class="spacing"/>
  </div>
</template>

<script>
</script>

<style scoped>
.spacing{
  width: 100vw;;
  height: 20px;
}
.page{
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0px;
  gap: 24px;

  position: relative;
  width: 100%;

  background: #F9F9F9;
}
</style>
