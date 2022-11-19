<template>
  <div class="card">
    <slot/>
  </div>
</template>

<style scoped>
.card{
  /* Auto layout */

  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 12px;

  width: 567px;

  background: #FFFFFF;
  box-shadow: 0px 4px 16px rgba(0, 0, 0, 0.1);
  border-radius: 12px;

  /* Inside auto layout */

  /*flex: none;*/
  /*flex-grow: 0;*/
}
</style>
