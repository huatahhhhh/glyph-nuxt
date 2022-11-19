<template>
  <div class="logocontainer center"> 
    <div class="logo mx-auto"/>
  </div>
</template>

<script>
export default {

}
</script>

<style>
.logocontainer{
  /*width: 107px;*/
  /*height: 46px;*/

  /*[>[> Inside auto layout <]<]*/

  flex: none;
  flex-grow: 0;
}
.logo{
  margin-top: 4px;
  width: 81.74px;
  height: 32px;
  /*left: calc(50% - 81.74px/2 + 0.74px);*/
  /*top: calc(50% - 32px/2);*/

  background: url(assets/static/logo.png);
}

</style>
