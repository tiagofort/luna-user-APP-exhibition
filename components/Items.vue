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
        <v-btn @click="openItens('all')" large color="#b86935" class="white--text custom-btn btn">View All<div class="dot"></div></v-btn>
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
  height: 40px;
  color: #fff;
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
  border: none;
  background: #b86935;
    background: linear-gradient(0deg, #b37851 0%, #b86935 100%);
    color: #fff;
    overflow: hidden;
}
.btn:hover {
    text-decoration: none;
    color: #fff;
}
.btn:before {
    position: absolute;
    content: '';
    display: inline-block;
    top: -180px;
    left: 0;
    width: 30px;
    height: 100%;
    background-color: #fff;
    animation: shiny-btn1 3s ease-in-out infinite;
}
.btn:hover{
  opacity: .7;
}

.btn:active{
  box-shadow:  4px 4px 6px 0 rgba(255,255,255,.3),
              -4px -4px 6px 0 rgba(116, 125, 136, .2), 
    inset -4px -4px 6px 0 rgba(255,255,255,.2),
    inset 4px 4px 6px 0 rgba(0, 0, 0, .2);
}


@-webkit-keyframes shiny-btn1 {
    0% { -webkit-transform: scale(0) rotate(45deg); opacity: 0; }
    80% { -webkit-transform: scale(0) rotate(45deg); opacity: 0.5; }
    81% { -webkit-transform: scale(4) rotate(45deg); opacity: 1; }
    100% { -webkit-transform: scale(50) rotate(45deg); opacity: 0; }
}

</style>