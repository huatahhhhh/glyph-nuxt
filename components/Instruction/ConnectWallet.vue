<script setup>
const connected = useState("MM_connected");
</script>
<template>
  <instruction-card> 
    <div class="connectwallet">
      <div class="textcontainer">Connect Your Wallet</div>
    </div>
    <div class="connectbutton">
      <metamask-button/>
    </div>
  </instruction-card> 
</template>

<script setup>
</script>

<style scoped>
.connectwallet{
  /* Auto layout */

  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 12px;
  gap: 10px;

  width: 543px;
  height: 39px;


  /* Inside auto layout */

  flex: none;
  align-self: stretch;
  flex-grow: 0;
}
.connectbutton{
  /* Frame 11 */


  /* Auto layout */

  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 12px 12px 12px 27px;
  gap: 10px;

  width: 543px;
  height: 53px;


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
</style>
