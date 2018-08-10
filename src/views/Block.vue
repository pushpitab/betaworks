<template>
<div>
<!-- <div class="card">
     <h5 class="card-header"> {{ msg }}</h5>
     <div class="card-body" >

    <p class="input-group">
    <label for="block1chain1number" class="col-sm-1 control-label">Block:</label>
    <span class="input-group-addon">#</span>
    <input id="block1chain1number" type="number"
        v-model="inputBlock"
        v-on:input="updateHash"
    class="form-control">
    </p>
  </div>
</div> -->
    <!-- --------------------- START --------------------- -->
    <div class="container">
        <h1>{{ msg }}</h1>
         <div id="block1chain1well" v-bind:class="setClass">
            <form class="form-horizontal">
                <div class="form-group">
                    <label for="block1chain1number" class="col-sm-2 control-label">Block:</label>
                    <div class="col-sm-10">
                        <div class="input-group">
                            <span class="input-group-addon">#</span>
                            <input id="block1chain1number" type="number"
                             v-model="inputBlock"
                             v-on:input="updateHash"
                            class="form-control">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <label for="block1chain1nonce" class="col-sm-2 control-label">Nonce:</label>
                    <div class="col-sm-10">
                        <input id="block1chain1nonce" type="text"
                         v-model="inputNonce"
                         v-on:input="updateHash"
                        class="form-control">
                    </div>
                </div>
                <div class="form-group">
                    <label for="block1chain1data" class="col-sm-2 control-label">Data:</label>
                    <div class="col-sm-10">
                        <textarea id="block1chain1data" rows="10"
                        v-model="inputBlockData"
                        v-on:input="updateHash"
                         class="form-control"></textarea>
                    </div>
                </div>
                <div id="state" class="form-group">
                    <label for="block1chain1hash" class="col-sm-2 control-label">Hash:</label>
                    <div class="col-sm-10">
                        <input id="block1chain1hash" type="text" disabled class="form-control"
                         v-model="hashValue">
                    </div>
                </div>

                <div class="form-group">
                    <label for="identicon" class="col-sm-2 control-label">Identicon:</label>
                    <div class="col-sm-10">
                        <div id="identicon"></div>
                        <div id="roundIcon" class="identicon"
                        :style="{ backgroundImage: `url('${srcURL}')` }"></div>
                    </div>
                </div>

                <div class="form-group">
                    <div class="col-sm-2">
                        <i class="icon-spinner icon-spin icon-large"></i>
                    </div>
                    <div class="col-sm-10">
                        <button id="block1chain1mineButton" data-style="expand-right" 
                        class="btn btn-primary ladda-button"
                        v-on:click="processMine">
                            <span class="ladda-label">Mine</span>
                        </button>
                    </div>
                </div>
            </form>
        </div>
    </div>
    <!-- --------------------- END --------------------- -->

  </div>
</template>

<script>
export default {
  name: 'Block',
  data: function() {
    return {
      msg: 'Basics: Block',
      inputData: '',
      inputBlock:'1',
      inputNonce:'',
      inputBlockData:'',
      difficulty:4,
      maximumNonce:500000,
      activeClass:'well-success',
      errorClass:'well-error',
      isActive:true,
      hashValue:'',
      srcURL:''
    }
  },
  created:function(){
        this.processMine();
  },
  computed:{
    setClass: function(){
        console.log("setclass computed");
        if(this.isActive)
        return this.activeClass
        else{
             return this.errorClass
        }
    }
  },
  methods : {
    updateHash: function() {
      console.log("\n\n!!!!!!updateHash ");    
      this.isActive=false 
      var value = this.inputBlock+this.inputNonce+this.inputBlockData;
       console.log("updateHash value="+value);
      var hash = CryptoJS.SHA256(value).toString();
      console.log(hash);
      //document.getElementById('block1chain1hash').value = hash;
      this.hashValue=hash;
      // If you want rounded and diagonals
      this.srcURL=hqx(blockies.create({ seed: this.hashValue ,size: 8,scale: 3}),4).toDataURL();      
    },
    processMine: function() {
        console.log("\n\n!!!!!!processMine ");     
       this.mineBlock(this.difficulty);
    
    },
    mineBlock:function(difficulty) {
        console.log("\n\n!!!!!!mineBlock "); 
        var nonce=0;
        while (this.hashValue.substring(0, difficulty) !== Array(difficulty + 1).join("0")&& nonce<this.maximumNonce) {
            nonce++;
            this.hashValue = this.calculateHash(nonce);
        }

        console.log("BLOCK MINED: " + this.hashValue);
        this.inputNonce=nonce;
        this.isActive=true;
        this.srcURL=hqx(blockies.create({ seed: this.hashValue ,size: 8,scale: 3}),4).toDataURL();
    
    },
    calculateHash:function(nonce){
        var value = this.inputBlock+nonce+this.inputBlockData;
        var hash = CryptoJS.SHA256(value).toString();
        return hash;
    }
  }

}
</script>
<style scoped>


.well-success {
  background: rgb(223, 240, 216);
}

.well-error {
  background: rgb(250, 220, 220);
}

</style>
