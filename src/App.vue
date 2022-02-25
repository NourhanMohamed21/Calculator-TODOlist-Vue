<template>
  <div id="app" class="container-fluid">
    <div id="nav">
      <router-link class="" to="/">Calculator</router-link> |
      <router-link class="" to="/TODO">TODO</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
 #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
} 
 
#nav {
  padding: 30px;
  background-image: url();
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
   text-decoration: none;
   padding: 0.5%;
}

#nav a.router-link-exact-active {
  color: rgb(74, 74, 228);
  text-decoration: none;
 border:  rgb(74, 74, 228);;
 border-style:  solid;
 
} 
</style>
