<template>
  <div>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Hash/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Hash from '@/components/Hash.vue'

export default {
  name: 'home',
  components: {
    HelloWorld, Hash
  }
}
</script>
