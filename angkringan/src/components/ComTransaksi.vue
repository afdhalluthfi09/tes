<template>
  <div>
     <v-simple-table height="300px">
         <template v-slot:default>
        <tr>
            <td>id pesan : # {{idPesan}}</td>
            <td></td>
        </tr>
        <tr>
            <td>tanggal pemesanan</td>
            <td>{{tgl}}</td>
        </tr>
        <tr>
            <td>no.</td>
            <td>nama item</td>
            <td>harga</td>
            <td>jumlah pesan</td>
            <td>harga tot</td>
            <td>notes</td>
        </tr>
        <tr v-for="(item, index) in card" :key="item.id">
            <td>{{index+1}}</td>
            <td>{{ item.item }}</td>
            <td>{{ item.harga }}</td>
            <td>{{ item.qty}}</td>
            <td>{{ item.qty * item.harga }}</td>
            <td>{{ item.keterangan }}</td>
        </tr>
        <tr>
            <td>jumlah pesanan</td>
            <td>{{ jml }}</td>
        </tr>
        <tr>
            <td>harga total :</td>
            <td>{{jumlhTot}}</td>
        </tr>
         </template>
     </v-simple-table>
     <v-btn>batal</v-btn>
     <v-btn to="/selesai">lunas</v-btn>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
    computed: {
        ...mapGetters(["card"]),
        jumlhTot(){
            return this.card.reduce( (a, b) => a + b.qty * b.harga, 0)
        },
        jml(){
            return this.card.reduce( (a, b) => a + b.qty, 0)
        },
        tgl(){
            return Date()
        },
        idPesan(){
            return Math.floor(Math.random()*300)
        }
    }
}
</script>

<style>
</style>
