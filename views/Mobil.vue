<template>
  <v-app>
<NavBar />
<v-container fluid>
  <v-card
        color="#F7F7F7"
        height="180px"
        tile
        flat
        class="d-flex align-center justify-center mt-12"
        dark
      >
      </v-card>
      <v-divider class=mt-2></v-divider>
      <v-row>
          <v-col cols="12" sm="3" v-for="unit in get_unit_all_tayang" :key="unit.id" >
              <v-card height="300" align="center" flat outlined tile>
                <template v-for="photo in unit.unit_photo" :key="photo.id_unit">
                  <strong>{{photo.nama}}</strong>
                </template>
                <v-card-text class="mt-n1">
                  <strong>{{unit.nama}}</strong>
                </v-card-text>
                <v-card-text class="mt-n4">
                  <strong>Rp. {{unit.harga}}</strong>
                </v-card-text>
                <router-link class="btn btn-primary" :to="'/mobil/'+unit.id">Lihat Detail</router-link>
              </v-card>
          </v-col>
      </v-row>
      <v-divider></v-divider>
</v-container>
<FooterView />
  </v-app>
  
</template>

<script>

// Components
import NavBar from '@/components/NavBar.vue';
import FooterView from '@/components/FooterView.vue';
import axios from 'axios';
export default({
  name: 'Mobil',
data(){
  return {
    get_unit_all_tayang : [] 
  }
}, 
  components: {
    NavBar,
    FooterView
},
async mounted(){
     this.load()
    },

    methods:{
      async load(){
        const response =  await axios.get('https://api-nnd.sitama.co.id/api/v1/get_unit_all_tayang')
        this.get_unit_all_tayang = response.data.data
      }
    }
});
</script>
<style scoped>
  .v-container{
    width: 100%;
    padding: 16px 0px !important;
    margin-right: auto;
    margin-left: auto;
  }
  .v-card.borderme {
    border: 2px solid black !important;
  }
  .v-card.borderout {
    border: 1px solid #d5f0db !important;
  }
</style>