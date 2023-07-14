<template>
    <v-container class="fundo" color="#0b0418">
      <Autenticacao class="mb-5" textoBotao="Login" :submeterForm="logarUsuario"/>
    </v-container>
</template>

<script>
import Autenticacao from '@/components/Autenticacao.vue';

export default {
  data: () => ({
        
  }),
     components:{
    Autenticacao
  },
     methods:{
      async logarUsuario(loginInfo){
        try{
          await this.$auth.loginWith('local', {
               data: loginInfo
          })
          this.$notifier.showMessage({ content: 'Welcome back! Thanks for logged in', color: 'green', time: 2000 });
        }catch {
          this.$notifier.showMessage({ content: 'Something went wrong! Please, try again', color: 'red', time: 2000 });
        }
        
      }
     }
}

</script>
<style>
.fundo{
    background-color: #ffffff;
}

</style>