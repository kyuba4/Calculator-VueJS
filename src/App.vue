<template>
   <div id="app">
      <router-view />
   </div>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap");

* {
   margin: 0;
   padding: 0;
   box-sizing: border-box;
   font-family: "Poppins", sans-serif;
}

html {
   height: 100%;
}

body {
   height: 100%;
   background: #e0eafc;
   background: linear-gradient(to right, #cfdef3, #e0eafc);
   padding-top: 30px;
}
</style>
