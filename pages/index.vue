<template>
  <v-container fluid class="text-center pr-0 pl-0 mr-n2 mt-n8">
      <MainBanner />
          <v-container :max-width="getMaxWidth" class="text-center fundo">
              <v-row justify="center" class="mb-5">
                    <v-col>
                          <v-sheet class="pa-1">
                              <Items />
                          </v-sheet>
                    </v-col>
               </v-row> 
               <v-row class="mb-5">
                    <v-col sm="12" md="6" lg="4" align-self="start">
                          <v-sheet class="pa-1">
                              <Featured />
                          </v-sheet>   
                    </v-col>
                    <v-col sm="12" md="6" lg="8">
                          <v-sheet class="pa-1">
                              <Stones />
                          </v-sheet>          
                    </v-col>  
               </v-row>
               <v-row>
                    <v-col cols="12">  
                        <v-sheet height="100"></v-sheet>
                    </v-col>
               </v-row>
          </v-container> 
</v-container>
</template>

<script>
import img from '@/static/general/comingSoon.png';
import MainBanner from '../components/MainBanner.vue';
import Items from '../components/Items.vue';
import Featured from '../components/Featured.vue';
import Stones from '../components/Stones.vue';

export default {
    data () {
      return {
        slide: [],
        novidades: [],
        maisVendidos: [],
        model: null,
        imagem: img
      }
    },
    components: {
      MainBanner, Items, Featured, Stones
    },
    computed:{
      getMaxWidth (){
        return this.$vuetify.breakpoint.width - (this.$vuetify.breakpoint.width * 0.2);
      }
    },
    mounted() {
      this.initializeSlides();
      this.initializeNovidades();
      this.topVendaProdQtd();
    },
    methods:{
    initializeSlides() {
      this.$axios
        .get("/slide/buscarSlides")
        .then((response) => (this.slide = response.data));
    },
    initializeNovidades(){
      this.$axios
        .get("/item/buscarNovidades")
        .then((response) => (this.novidades = response.data));
    },
    topVendaProdQtd() {
      this.$axios
         .get(`/venda/topProdQtd/0`)
         .then((response) => {
                  this.maisVendidos = response.data});
    },
    carregarItem(id) {
          this.$router.push({
            name: "accessories-acessories",
            params: { acessories: id },
          });
    },
    carregarProduto(id){
        this.$router.push({
            name: "accessories-acessories",
            params: { acessories: id },
        });
    },    
  }
}
</script>

<style>
.fundo {
  background-color: #ffffff;
}

.texts {
    color: #b86935;
}
</style>
