<template>
  <nav class="topnav">
    <div class="menucontainer">
      <NuxtLink to="/">
         <nav-menu-item>
          Register
        </nav-menu-item>
      </NuxtLink>

      <!--
      <NuxtLink to="/scoreboard">
        <nav-menu-item>
          Leaderboard
        </nav-menu-item>
      </NuxtLink>
      -->
    </div>
    <nav-logo/>
    <div class="buttoncontainer">
      <metamask-button/>
    </div>
  </nav> 
</template>

<style>
.topnav{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 9px 25px;
  gap: 192px;

  width: 100%;
  height: 100%;

  background: #FFFFFF;

  /* Inside auto layout */

  flex: none;
  order: 0;
  flex-grow: 0;
}

.menucontainer{
  /* Auto layout */
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 0px;
  gap: 20px;


  /* Inside auto layout */
  flex: none;
  order: 0;
  flex-grow: 0;
}
.buttoncontainer{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-end;
  padding: 0px;
  gap: 10px;

  width: 320px;
  height: 40px;
}
</style>
