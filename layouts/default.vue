<template>
  <v-app id="inspire">
    <MenuBar />
        <v-main class="fundo" fluid>
            <v-container fluid class="px-0 ma-2">
              <v-row>
                <v-col
                  cols="12"
                  class="px-0"
                >
                    <nuxt />
                </v-col>
              </v-row>
            </v-container>     
        </v-main>
    <SnackBar />
    <Footer />
  </v-app>
</template>

<script>
import MenuBarVue from '~/components/MenuBar.vue';
import SnackBar from '~/components/SnackBar.vue';
import Footer from '~/components/Footer.vue';
  export default {
    data: () => ({
      links: [
        {
          icon: 'mdi-home-heart',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-necklace',
          title: 'Accessories',
          to: '/accessories/all'
        },
        {
          icon: 'mdi-information-variant',
          title: 'About Us',
          to: '/about_us'
        }
      ],
    }),
    components:{ MenuBarVue, SnackBar, Footer }
  }
</script>

<style>
.fundo{
  background-color: #ffffff;
}

.no-elevation {
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
}
</style>