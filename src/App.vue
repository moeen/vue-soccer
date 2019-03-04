<template>
  <div id="app">
    <div class="head">
      <img src="./assets/logo.png" alt="logo">
      <h1>Vue Soccer</h1>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
body {
  background-color: #e3f2fd;
}
#app {
  font-family: 'Vazir', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.head {
  display: flex;
  flex-wrap: nowrap;
  justify-content: center;
  img {
    height: 80px;
    width: 80px;
  }
}
</style>
