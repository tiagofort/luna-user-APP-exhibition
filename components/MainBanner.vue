<template>
    <v-banner
        color="#FFFFFF"
        dark
        class="ml-n7 mr-n8 pr-0 pl-0"
    >
      <v-responsive
        :aspect-ratio="getAspectRatio"
      >
        <v-img
             :max-width="getMaxWidth"
             :max-height="getMaxHeight" 
             :src="bannerImage"
             alt="Banner Image"
             class="pr-0" 
        ></v-img>
      </v-responsive>
    </v-banner>
  </template>
  
  <script>
  import banner from '@/static/banner/banner_temp.jpeg';
  export default {
    data() {
      return {
        aspectRatio: 2 / 1,
        bannerImage: banner
      };
    },
    computed:{
        getMaxWidth() {
           return this.$vuetify.breakpoint.width; 
        },
        getMaxHeight() {
        },
        getAspectRatio() {
            if (this.$vuetify.breakpoint.width < 600) {
                return 2 / 1;
            } else {
                return 3 / 1;
            }
        }
    }
  };
  </script>
  
  <style>
  .v-banner {
    height: auto;
  }

  .no-elevation {
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
  }

  </style>
  
  
  
  
  
  
  