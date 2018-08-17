<template>
  <div>

    <Navigation v-bind:msg="navigation"/>    
    <router-view></router-view>

  </div>
</template>

<script>

import Navigation from '@/components/blockchain/Navigation.vue'

export default {
  name: 'Blockchain',
  components: {
      Navigation
  },
  methods : {
    getNavigation : function(){
        var path = this.$route.path;
        console.log('in getNavigation path: ' + path);

        // blockchain basics components
        var basics = [
            '/blockchain/hash',
            '/blockchain/block',
            '/blockchain/chain',
            '/blockchain/distributed',
            '/blockchain/tokens',
            '/blockchain/coinbase'
        ];
        for (var url of basics){
            if(path === url){
                console.log('matched BasicsNavigation');                
                return 'BasicsNavigation';
            }
        }

        // blockchain keys components
        var keys = [
            '/blockchain/keys',
            '/blockchain/signatures',
            '/blockchain/transaction',
            '/blockchain/chain2'
        ];
        for (var url of keys){
            if(path === url){
                console.log('matched KeysNavigation');
                return 'KeysNavigation';
            }
        }

        // blockchain live components
        var live = [
            '/blockchain/transfer',
            '/blockchain/track',
            '/blockchain/contract',
            '/blockchain/currency'
        ];
        for (var url of live){
            if(path === url){
                console.log('matched LiveNavigation');                
                return 'LiveNavigation';
            }
        }        
    }
  },
  data: function(){
    console.log('path: ' + this.$route.path);
    var navigation = this.getNavigation();
    console.log('navigation: ' + navigation);
    return { navigation };  
  },
  watch:{
      $route (to, from){
          var path = this.getNavigation();
          console.log(path);        
          this.navigation = path;
      }
  }  

}
</script>