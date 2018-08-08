<template>
  <div id="app">

    <Navigation/>
    <div class="container" style="margin-top:20px">    
      <div id="nav">
        <router-link to="/">Home</router-link> |
        <router-link to="/about">About</router-link>|
        <router-link to="/block">Block</router-link>
      </div>
      <router-view/>
    </div>

  </div>
</template>

<script>
    import Navigation from './components/Navigation.vue'

    export default {
     name: 'app',
     components:{
        Navigation
     }
    }
</script>
