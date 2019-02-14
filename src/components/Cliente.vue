<template>
  <div class="seccion">
    <div class="atributo">
      <span>{{ nomeCompleto }}</span>
    </div>
    <div class="atributo">
      <img :src="fotoPerfil" alt="">
    </div>
    <div class="atributo">
      <a :href="biografia" target="_blank">Biografia</a>
    </div>
    <div class="atributo">
      <span>Idade: {{ idade }}</span>
    </div>
    <div class="atributo">
      <span>{{ email }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: ['email'],
  data() {
    return {
      nomes: "Washington",
      sobrenome: "Cardoso",
      dataNascimento: new Date(1986, 5, 4),
      fotoPerfil: 'https://upload.wikimedia.org/wikipedia/commons/thumb/3/39/GodfreyKneller-IsaacNewton-1689.jpg/200px-GodfreyKneller-IsaacNewton-1689.jpg',
      biografia: 'https://pt.wikipedia.org/wiki/Isaac_Newton'
    };
  },
  computed: {
      nomeCompleto() {
          return `${this.nomes} ${this.sobrenome}`
      },
      idade() {
          return this.calcularIdade(this.dataNascimento)
      }
  },
  methods: {
    calcularIdade(dataNascimento) {
      let dataAtual = new Date();
          let diferenca = dataAtual - dataNascimento;
          return Math.floor(diferenca / (1000 * 60 * 60 * 24 *365.25))
    }
  },
  created() {
    this.$emit('onMudarEmail', 'newton@email.com')
  }
};
</script>


<!-- escoped: utilizando o scoped o estilo so sera utilizado por este component  -->
<style scoped>


</style>