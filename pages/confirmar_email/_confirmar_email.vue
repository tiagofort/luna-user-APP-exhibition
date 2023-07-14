<template>
    <v-container class="fundo mt-5">
        <v-row class="mt-5">
            <v-col></v-col>
            <v-col class="text-center">
                <span class="white--text text-h5">Thansk for confirming your email!</span><br>
                <span class="white--text text-h5">Click on the button to go to the Login Page</span><br>
                <v-btn class="mt-5" @click="redirecionar()">Login</v-btn>
            </v-col>
            <v-col></v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
  data: () => ({
        
  }),
     methods:{
        redirecionar(){
            this.$router.push({
                name: "login",
            });
        },
        async confirmarEmail(){
            var email = window.location.href.split('=')[1];
            await this.$axios
                            .$put(`/usuario/confimar_email`, {
                               email: email
                            })
                            .then((response) => {
                              console.log("Success");
                            })
                            .catch((error) => {
                              console.log(error);
                              this.$notifier.showMessage({ content: 'Something went wrong! Please, refresh the page and try again!', color: 'green', time: 2000 });
                            });
        }
     },
     mounted(){
        this.confirmarEmail();
     }
}
</script>

<style>
.fundo {
  background-color: #0b0418;

}
</style>