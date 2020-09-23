<template>
  <div>
     <v-simple-table height="300px">
         <template v-slot:default>
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
            <td>{{ jmlhTot }}</td>
            <td>{{ item.keterangan }}</td>
        </tr>
         </template>
     </v-simple-table>
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
        }
    }
}
</script>

<style>
</style>
