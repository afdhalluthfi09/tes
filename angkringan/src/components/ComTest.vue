<template>
  <div>
      <div class="list">
          <h5>ID Pesan : <span>#534553</span></h5>
          <span class="font">{{tanggal}}</span>
          <v-btn @click="papTT()">tekan</v-btn>
      </div>
      <hr>

      <table>
          <tr>
              <td>id</td>
              <td>nama_item</td>
              <td>harga_item</td>
              <td>jumlah_item</td>
              <td>harga total</td>
              <td>keteranagan</td>
          </tr>
          <tr v-for="item in card" :key="item.id">
              <td>{{item.id}}</td>
              <td>{{item.item}}</td>
              <td>{{item.harga}}</td>
              <td>{{itm.qty}}</td>
              <td>{{item.keterangan}}</td>
          </tr>
      </table>
  </div>
</template>

<script>
import {mapGetters} from 'vuex'
export default {
    computed:{
        ...mapGetters(["trans"]),
        tanggal(){
            return Date()
        },
    props:["card"]
        
    },
    methods:{
        papTT(){
            console.log("anak anjing")
        }
    }
    

}
</script>

<style scoped>

    .list{
        width: 300px;
        border: 5px solid salmon;
        
    }
    .list > h5{
        color: salmon;
        text-align: center;
        line-height: 42px;
    }
    .font{
        color: salmon;
        text-align: center;
    }
    table td{
        border: 5px solid black;
        
    }
    td{
        margin-left: 25px;
    }
    
    
</style>