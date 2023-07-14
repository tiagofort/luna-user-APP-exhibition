<template>
    <v-footer
      v-bind="configFooter"
      color="#ffe2d4"
      padless
      class="mt-5"
    >
      <v-row
        justify="center"
        no-gutters
      >
      <strong class="mt-4">Connect with Luna Instagram</strong>
        <v-btn
          color="#b86935"
          icon 
          class="my-2"
          @click="openIntagram(icons.url)"
        >
         <v-icon>
            {{ icons.icon }}
         </v-icon>
        </v-btn>
        <v-col
          class="#e9dcd3 py-4 text-center"
          cols="12"
        >
        <v-divider></v-divider>
          <span class="mt-1">{{ new Date().getFullYear() }} — Developer - Tiago Gai</span>
          <v-btn icon color="#b86935" @click="openIntagram('https://www.instagram.com/tiagofort/')">
            <v-icon>mdi-instagram</v-icon>
          </v-btn>
            <v-tooltip top>
                <template v-slot:activator="{ on, attrs }">
                    <v-icon color="#b86935" v-bind="attrs" v-on="on">
                        mdi-home
                    </v-icon>
                </template>
                <span>tiagofortalezag@gmail.com</span>
            </v-tooltip>
        </v-col>
      </v-row>
    </v-footer>
  </template>

<script>
export default {
  data: () => ({
    icons: 
        {
            icon: 'mdi-instagram',
            url: 'https://www.instagram.com/lunapedraria.ie/'
        }
  }),
  methods:{
    openIntagram(url){
        window.open(url, '_blank');
    }
  },
  computed: {
    configFooter(){
        const config = {};
        if(this.$vuetify.breakpoint.width < 600){
            config.absolute = false;
            config.app = true;
        }else{
            config.absolute = true;
            config.app = false;
        }
        return config;
    }
  }
}
</script>

<style>
.texts {
    color: #b86935;
}
</style>