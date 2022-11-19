<template>
  <button class="menubutton">
    <div class="menutextcontainer">
      <div class="menutext">
        <slot></slot>
      </div>
    </div>
    <div class="colorbar">
    </div>
  </button>
</template>

<script>
export default {

}
</script>

<style>
.menubutton{
  /* Menu Button */


  /* Auto layout */

  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0px;
  gap: 1px;

  width: 93px;
  height: 44px;

  background: #FFFFFF;

  /* Inside auto layout */

  flex: none;
  order: 0;
  flex-grow: 0;
}

.menutextcontainer{
  /* Auto layout */

  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 12px 8px;

  /*width: 93px;*/
  /*height: 39px;*/

  background: #FFFFFF;

  /* Inside auto layout */

  flex: none;
  align-self: stretch;
  flex-grow: 0;
}

.menutext{
  /*font-family: 'Inter';*/
  /*font-style: normal;*/
  /*font-weight: 700;*/
  font-size: 16px;
  line-height: 15px;
  /* identical to box height */

  text-align: center;

  color: #000000;


  /* Inside auto layout */

  flex: none;
  flex-grow: 0;
}

.colorbar{
  background: #FAEA48;

  /* Inside auto layout */
  
  height: 4px;
  width: 100%;

  /*flex: none;*/
  /*align-self: stretch;*/
}
</style>
