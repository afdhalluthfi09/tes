<template>
  <div>
    <v-row justify="center">
      <v-dialog v-model="dialog" persistent max-width="800">
        <template v-slot:activator="{ on, attrs }">
          <v-btn color="primary" dark v-bind="attrs" v-on="on">Pesan Sekarang</v-btn>
        </template>
        <v-card>
          <v-card-title class="headline">Transaksi Kamu</v-card-title>
          <v-simple-table height="300px">
            <template v-slot:default>
              <thead>
                <tr>
                  <th class="text-left">No</th>
                  <th class="text-left">Item</th>
                  <th class="text-left">Keterangan</th>
                  <th class="text-left">Jumlah</th>
                  <th class="text-left">Harga Satuan</th>
                  <th class="text-left">Harga Total</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(item, index) in card" :key="item.id"  >
                  <th>{{ index+1}}</th>
                  <td>{{ item.item }}</td>
                  <td>{{ item.keterangan }}</td>
                  <td>{{ item.qty }}</td>
                  <td>Rp. {{ item.harga }}</td>
                  <td>Rp. {{ item.qty * item.harga }}</td>
                </tr>
                <tr>
                  <td colspan="2">Total</td>
                  <td></td>
                  <td>{{ jumlahPesanan }}</td>
                  <td></td>
                  <td>Rp. {{ total }}</td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="primary" text @click="dialog = false">Batal</v-btn>
            <v-btn color="primary" text @click="pushTrans(item.id)" to="./transaction_success">Lanjutkan</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
  </div>
</template>

<script>
import { mapGetters} from "vuex";
export default {
  data() {
    return {
      dialog: false
    };
  },
  computed: {
    ...mapGetters(["card"]),
    total() {
      return this.card.reduce((a, b) => a + b.qty * b.harga, 0);
    },
    jumlahPesanan() {
      return this.card.reduce((a, b) => a + b.qty, 0);
    },
    ambil(){
      return this.$store.getters.card
    }
    
   }
};
</script>

<style>

</style>
