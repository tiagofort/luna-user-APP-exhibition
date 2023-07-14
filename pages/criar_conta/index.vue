<template>
    <v-container class="fundo">
        <CadastroUsuario textoBotao="Create" :submeterForm="salvarUsuario" />
    </v-container>
</template>

<script>
import CadastroUsuario from '@/components/CadastroUsuario.vue';
export default {
  data: () => ({
        
  }),
     components:{
        CadastroUsuario
  },
     methods:{
        async salvarUsuario(usuInfo){
            await this.$axios
                            .$post(`/usuario/salvar_cliente`, {
                               nome: usuInfo.nome,
                               sobrenome: usuInfo.sobrenome,
                               email: usuInfo.email,
                               phone: usuInfo.phone,
                               senha: usuInfo.senha,
                               avatar: usuInfo.avatar
                            })
                            .then((response) => {
                              console.log("Success");
                              this.$notifier.showMessage({ content: 'Account created! You are more than welcome!', color: 'green', time: 2000 });
                              this.$router.push({
                                 name: "index",
                              });
                            })
                            .catch((error) => {
                              console.log(error);
                              this.$notifier.showMessage({ content: 'Something went wrong! Please, refresh the page and try again!', color: 'green', time: 2000 });
                            });
            }
     }
}


</script>

<style>
.fundo {
  background-color: #ffffff;

}

</style>