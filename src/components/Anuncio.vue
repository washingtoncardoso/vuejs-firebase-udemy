<template>
  <div class="anuncio">
    <!--
        <span v-once>
            {{ apresentacoes[indice] }}
        </span>
    -->
    <transition name="fade" mode="out-in">
        <span v-for="(apresentacao, index) in apresentacoes" :key="index">
            {{ apresentacao }}
        </span>
    </transition>
  </div>
</template>


<script>
export default {
  data() {
    return {
      apresentacoes: [
        "Hamilton - 20:30",
        "Frozen - 15:00",
        "Anastasia - 14:00",
        "El Rey Leon - 22:00"
      ],
      indice: 0
    };
  },
  methods: {
    mostrarAnuncio() {
      this.indice++;

      /*
            if (this.indice == this.apresentacoes.length) {
                this.indice = 0
                this.$destroy()
            }
            */

      if (this.indice == this.apresentacoes.length) {
        this.indice = 0;
      }
    },
    mounted() {
      console.log("mounted");
      setInterval(this.mostrarAnuncio, 3000);
    }
  }
}
</script>

<style>
.anuncio {
  font-size: 2rem;
  margin: 10px;

  border-top-color: white;
  border-top-width: 1px;
  border-top-style: solid;

  border-bottom-color: white;
  border-bottom-width: 1px;
  border-bottom-style: solid;
}

.fade-enter {
  opacity: 0;
}

.fade-enter-active {
  transition: opacity 1s ease-out;
}

.fade-leave-active {
  transition: opacity .6s ease-out;
}

.fade-leave {
  opacity: 0;
}
</style>