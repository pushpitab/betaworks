<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <div v-if="msg === 'BasicsNavigation'">
      <BasicsNavigation/>
    </div>
    <div v-else-if="msg === 'KeysNavigation'">
      <KeysNavigation/>
    </div>
    <div v-else-if="msg === 'LiveNavigation'">
      <LiveNavigation/>
    </div>    
    <div v-else>
      <!-- do nothing -->
    </div>

  </div>
</template>

<script>

import BasicsNavigation from '@/components/blockchain/basics/Navigation.vue'
import KeysNavigation from '@/components/blockchain/keys/Navigation.vue'
import LiveNavigation from '@/components/blockchain/live/Navigation.vue'


export default {
  name: 'Navigation',
  components: {
      BasicsNavigation,KeysNavigation,LiveNavigation
  },  
  props: {
    msg: String
  }
}

</script>