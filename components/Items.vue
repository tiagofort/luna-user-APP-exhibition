<template>
  <v-container>
    <v-row>
      <v-col align-self="center">
       <p class="texts text-lg-h6">What is new?</p>
      </v-col>
    </v-row>
    <v-row>
      <v-col
        v-for="(item,i) in sliceItens"
        :key="i"
        :id="item._id"
        class="d-flex justify-center child-flex"
        :cols="getCols"
      >
        <v-sheet max-width="350">
          <v-hover>
            <template v-slot:default="{ hover }">  
              <a>
                <v-img
                  :src="hover? item.midia.url2 : item.midia.url1"
                  aspect-ratio="1"
                  max-width="350"
                  max-height="450"
                  class="grey lighten-2"
                  @click="openItem(item._id)"
                >
                </v-img>
              </a>  
            </template>
          </v-hover>
          <a @click="openItem(item._id)"><p class="texts text-left mt-2">{{ item.titulo + ' - ' + item.pedra }}</p></a>
          <p class="text-left mt-n2">{{ item.preco+'€' }}</p>
        </v-sheet>
      </v-col>
    </v-row>
    <v-row>
      <v-col align-self="center">
        <button @click="openItens('all')" color="#b86935" class="custom-btn btn">View All</button>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
    data() {
      return {
        aspectRatio: 2 / 1,
        novidades: []
      };
    },
    methods: {
      initializingItens(){
      this.$axios
        .get("/item/buscarNovidades")
        .then((response) => (this.novidades = response.data));
      },
      openItens(param){
        this.$router.push({
          name: "view_all-all",
          params: { all: param },
        });
      },
      openItem(id){
        this.$router.push({
          name: "accessories-acessories",
          params: { acessories: id },
        });
      }
    },
    computed:{
        getMaxWidth() {
           return this.$vuetify.breakpoint.width; 
        },
        getCols(){
           return this.$vuetify.breakpoint.mdAndUp ? 3 : 6;
        },
        sliceItens(){
            return this.novidades.slice(0,8);
        }
    },
    mounted() {
      this.initializingItens();
    }
  };
</script>

<style>
.texts {
    color: #b86935;
}

a {
    color: #b86935;
}

.custom-btn {
  width: 130px;
  height: 50px;
  color: #ffffff;
  padding: 10px 25px;
  font-family: 'Lato', sans-serif;
  font-weight: 500;
  background: transparent;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  display: inline-block;
  outline: none;
}

.btn {
  background: #b86935;
  border: 2px solid #b86935;;
  z-index: 1;
}

.btn:after {
  position: absolute;
  content: "";
  width: 0;
  height: 100%;
  top: 0;
  right: 0;
  z-index: -1;
  background-color: #ffffff;
  transition: all 0.3s ease;
}

.btn:hover {
  color: #b86935;
  border: 1px solid #b86935;
}

.btn:hover:after {
  left: 0;
  width: 100%;
}

.btn:active {
  top: 2px;
}

</style>