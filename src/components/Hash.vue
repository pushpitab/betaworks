<template>
  <div>
    <!-- --------------------- START --------------------- -->
    <div class="container">
        <h1>{{ msg }}</h1>
        <div id="well1" class="well">
            <form class="form-horizontal">
                <div class="form-group">
                    <label for="data" class="col-sm-2 control-label">Data:</label>
                    <div class="col-sm-10">
                        <textarea id="credit-limit-input" rows="10" v-model="inputData" v-on:input="processInputData" class="form-control"></textarea>
                    </div>
                </div>
                <div class="form-group">
                    <label for="hash" class="col-sm-2 control-label">Hash:</label>
                    <div class="col-sm-10">
                        <input id="hash" type="text" disabled class="form-control">
                    </div>
                </div>
                <div class="form-group">
                    <label for="identicon" class="col-sm-2 control-label">Identicon:</label>
                    <div class="col-sm-10">
                        <div id="identicon"></div>
                        <div id="roundIcon" class="identicon"></div>
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
  name: 'Hash',
  data: function() {
    return {
      msg: 'Basics: SHA256 Hash',
      inputData: ''
    }
  },
  methods : {
    processInputData : function(data){
      console.log(data);
      console.log(data.srcElement);
      console.log(data.srcElement.value);      
      var value = data.srcElement.value;
      var hash = CryptoJS.SHA256(value).toString();
      console.log(hash);
      document.getElementById('hash').value = hash;

      // If you want rounded and diagonals
      var roundIcon = document.getElementById('roundIcon');
      roundIcon.style.backgroundImage = 'url(' + hqx(blockies.create({ seed:hash ,size: 8,scale: 3}),4).toDataURL()+')';


    }
  }

}
</script>