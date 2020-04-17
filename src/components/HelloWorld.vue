<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  <div>
    <button class="a-v-button" @click="$emit('click')">
    <slot>Ini contoh untuk atoms,moleculs,organism</slot>
  </button><br><br>
        <input type="text" v-model="huruf_1"> +
        <input type="text" v-model="huruf_2">
        <h2 class="text-center">{{ huruf_1 + huruf_2}}</h2>

        <input type="text" :disabled="isDisabled">
        <button @click="isDisabled = !isDisabled">Enable/Disable</button><br><br>
         Masukkan tanggal <br><input type="date" v-model="tanggal_1">
    </div>
        <hr>
        <div class="cascading-dropdown">
        <div class="dropdown">
                <span>Propinsi:</span>
                <select v-model="selectedPropinsi">
                    <option value="">Pilih Provinsi</option>
                    <option v-for="(propinsi_obj, propinsi) in tempat" :value="propinsi" v-bind:key="propinsi">{{propinsi}}</option>
                </select>
            </div><br>
            <div class="dropdown">
                <span>Kota:</span>
                <select :disabled="kota.length == 0" v-model="selectedKota">
                    <option value="">Pilih Kota</option>
                    <option v-for="(kota_obj, kota) in kota"  v-bind:key="kota">{{kota}}</option>
                </select>
            </div><br>
             <textarea>Masukkan Alamat Disini !!!
             </textarea>
        </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<script>
new Vue({

  el: '#app',
  data: {
    isDisabled: false
  }

})
</script>

<script>
export default { data: function () {
  return { huruf_1: null, huruf_2: null
  },{
      tempat: {
        'Jawa Timur': {
          Surabaya: [],
          Malang: [],
          Gresik: [],
          Banyuwangi: [],
          Madiun: []
        },
        'Jawa Tengah': {
          Solo: [],
          Semarang: [],
          Magelang: [],
          Boyolali: [],
          Klaten: []
        }
      },
      kota: [],
      selectedPropinsi: '',
      selectedKota: ''
    }
  },
  watch: {
    selectedPropinsi: function () {
      // Clear previously selected values
      this.kota = []
      this.selectedKota = ''
      // Populate list of countries in the second dropdown
      if (this.selectedPropinsi.length > 0) {
        this.kota = this.tempat[this.selectedPropinsi]
      }
    },
    selectedKota: function () {
    }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.cascading-dropdown{
   text-align: center;
    margin-left: 400px;
    margin-right: 400px;
    margin-top: 30px;
    background-color: rgb(228, 218, 87);
    border-style: solid;
    border-color: rgb(0, 0, 0);
    align-content: center;
}
</style>
