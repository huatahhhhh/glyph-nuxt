<template>
  <div class="card">
    <div class="userheader">
      <div class="handlecontainer">
        <div class="handle">
          @elonmusk
        </div>
      </div>
      <div class="addresscontainer">
        <div class="address">
          0xE3B6D9e1fFAf1bfd98c2943ADd7c074a37bCA506 
        </div>
      </div>
    </div>
    <div class="scorerow1">
      <user-value-box param="hello" paramval="world"/>
      <user-value-box param="hello" paramval="world"/>
      <user-value-box param="hello" paramval="world"/>
    </div>
    <div class="spacing"/>
    <div class="scorerow1">
    </div>
    <div class="spacing2"/>
  </div>
</template>

<script setup>
</script>

<style scoped>
.card{
/* Auto layout */

display: flex;
flex-direction: column;
align-items: center;
gap: 14px;

width: 567px;
height: 308px;

background: #FFFFFF;
box-shadow: 0px 4px 16px rgba(0, 0, 0, 0.1);
border-radius: 12px;

/* Inside auto layout */

/*flex: none;*/
/*order: 2;*/
/*flex-grow: 0;*/
}

.userheader{
/* User */
  box-sizing: border-box;

  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 4px 12px;

  width: 100%;
  height: 80px;

  background: #8EDDFF;
  border-bottom: 1px solid #EFEFEF;
  border-radius: 12px;
}

.handlecontainer{
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 12px 12px 0px;
  gap: 10px;
  flex: none;
  align-self: stretch;
  flex-grow: 0;
}
.handle{
  font-style: normal;
  font-weight: 500;
  font-size: 20px;
  line-height: 24px;
  color: #000000;
  flex: none;
  order: 0;
  flex-grow: 0;
}
.addresscontainer{
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 0px 12px 12px;
  gap: 10px;
  /*width: 543px;*/
  height: 36px;
  flex: none;
  align-self: stretch;
  flex-grow: 0;
}
.address{
  font-style: italic;
  font-weight: 500;
  font-size: 12px;
  line-height: 24px;
  color: #000000;
  flex: none;
  flex-grow: 0;
  height: 24px;
}
.spacing1{
  width: 80%;
  height: 1px;
  background: #D1D1D1;
}
.spacing2{
  height: 19px;
  flex: none;
  align-self: stretch;
  flex-grow: 0;
}

.scorerow1{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
  padding: 0px;
  width: 100%;
  height: 76px;
}

</style>
