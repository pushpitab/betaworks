<template>
  <div class="hello">

    <!-- Navigation -->
    <Navigation/>          

    <h1>chain.vue</h1>

  </div>
</template>

<script>

import Navigation from '@/components/blockchain/basics/Navigation.vue'

export default {
  name: 'Chain',
  components: {
      Navigation
  }
}

</script>