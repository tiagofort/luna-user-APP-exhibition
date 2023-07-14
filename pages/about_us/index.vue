<template>
  <v-container class="mt-5">
          <v-row>
            <v-col class="text-center">
                <v-sheet>
                    <div class="text-h4 texts">About us</div>
                        <v-row>
                            <v-col class="pa-5 pb-1 mt-3 text-center">
                                <!-- <div class="text-center text-h4">{{ name }}</div><br> -->
                                <div class="text-justify text-h6 mt-3">{{ about_resume }}</div><br>
                            </v-col>
                        </v-row>
                        <!-- <v-row>
                            <v-col>
                                <div class="text-subtitle-1 text-xs-caption text-justify pa-2">{{ resume }}</div><br>
                            </v-col>
                        </v-row> -->
                </v-sheet>
            </v-col>
          </v-row>
  </v-container>  
</template>

<script>
export default {
  data() {
    return {
      about_resume: "If you believe in the energy of natural stones and crystals, you are in the right place! Luna Pedraria" +
                    " aims to be able to tune your vibrations with those of the chosen stones, improving and enhancing your energies"+
                    " in everyday life, supporting various aspects of well-being through unique and elegant accessories that will make"+
                    " you even more beautiful. Our jewellery are a great way to innovate and show your identity with style. Here you will"+
                    " find the greatest variety and quality of accessories with natural stones and crystals to give a special touch to your"+
                    " look. Being with us is an invitation to relax, intuit, transform, love yourself, find yourself and rediscover the most"+
                    " beautiful thing that lives in us. We want to share with the world the beauty and grandeur of these special elements that are crystals."+
                    " Check out everything we offer and start your experience in this crystalline universe!"
    };
  },
};
</script>

<style>
.texts {
  color: #b86935;
}
</style>