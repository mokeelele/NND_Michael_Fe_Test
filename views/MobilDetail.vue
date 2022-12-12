<template>
  <div class="mobil-detail">
    <NavBar />
    <div class="container">
        <div class="row mt-4">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link to="/" class="text-dark">Home</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link to="/mobil" class="text-dark">Mobil</router-link>
              </li>
              <li class="breadcrumb-item active" aria-current="page">Detail Mobil</li>
            </ol>
          </nav>
        </div>
      </div>

      <div class="row">
        <div class ="col md-6">

        </div>
        <div class ="col md-6">
            <h2><strong></strong></h2>
        </div>
    </div>
  </div>
  </div>
</template>

<script>
import NavBar from '@/components/NavBar.vue';
import axios from 'axios';
export default ({
    name: "MobilDetail",
    data(){
  return {
    get_unit_all_tayang : [] 
  }
},
    components:{
        NavBar,
    },
    async mounted(){
     this.load()
    },

    methods:{
      async load(){
        const response =  await axios.get("https://api-nnd.sitama.co.id/api/v1/get_unit_all_tayang"+this.$route.params.id)
        this.get_unit_all_tayang = response.data.data
      }
    }
});
</script>

<style>

</style>