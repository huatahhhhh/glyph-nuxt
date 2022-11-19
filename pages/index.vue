<script setup>
const connected=useState("MM_connected")
const twitterId = useState("twitter_id", ()=>null);
const twitterName = useState("twitter_name",()=>null);
const twitterIdSigned = useState("twitter_id_signed",()=>null);

</script>

<template>
  <div class="page h-screen"> 
    <div class="spacing"/>
    <instruction-connect-wallet>
    </instruction-connect-wallet>

    <instruction-enter-twitter v-if="connected">
    </instruction-enter-twitter>

    <instruction-request-sign v-if="twitterId && twitterName">
    </instruction-request-sign>

    <instruction-register-message v-if="twitterIdSigned">
    </instruction-register-message>


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
