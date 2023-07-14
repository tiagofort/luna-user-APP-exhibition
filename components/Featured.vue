<template>
  <v-container>
    <v-row v-if="slides.length > 0">
        <v-col class="ml-2">
            <p class="text-left texts text-lg-h6">Featured</p>
            <v-card
                elevation="24"
                max-width="450"
            >
                <v-carousel
                    :continuous="true"
                    :cycle="cycle"
                    :show-arrows="true"
                    hide-delimiter-background
                    delimiter-icon="mdi-minus"
                    height="450"
                >
                        <a>
                        <v-carousel-item
                            v-for="(slide, i) in slides"
                            :key="i"
                            :src="slide.url"
                            class="transparent"
                            @click="openFeatured(slide.id_produto)"
                        >
                        </v-carousel-item>
                        </a>
                </v-carousel>
            </v-card>
        </v-col>    
    </v-row>     
  </v-container>  
</template>

<script>
export default {
  data() {
    return {
        cycle: true,
        slides: [],
    }
  },
  methods:{
    initializeSlides() {
      this.$axios
        .get("/slide/buscarSlides")
        .then((response) => (this.slides = response.data));
      },
    openFeatured(id){
      console.log(id)
      this.$router.push({
          name: "accessories-acessories",
          params: { acessories: id },
      });
    }
  },
  mounted() {
    this.initializeSlides();
  }
}
</script>