<template>
  <div id="app" class="principal">

    <span>{{ titulo }}</span>
    <div>
      <button @click="componentAtual = item.nome" v-for="(item, index) in menu" :key="index" class="menu">{{ item.descricao }}</button>
    </div>
    <component :is="componentAtual"></component>
    
  </div>
</template>

<script>

import Entrada from '@/views/Entrada.vue'
import Home from '@/views/Home.vue'
import Login from '@/views/usuario/Login.vue'
import Perfil from '@/views/usuario/Perfil.vue'
import Registro from '@/views/usuario/Registro.vue'

export default {  
  name: 'App',
  data() {
    return {
      titulo: 'Entradas',
      componentAtual: 'entrada',
      menu: [
        { descricao: 'Home', nome: 'home' },
        { descricao: 'Entradas', nome: 'entrada' },
        { descricao: 'Perfil', nome: 'perfil' },
        { descricao: 'Login', nome: 'login' },
        { descricao: 'Registro', nome: 'registro' }
      ]
    }
  },
  components: { Entrada, Home, Login, Perfil, Registro }
}

</script>



<style>
html {
  font-size: 62.5% !important; /* 10px / 16px = 0.625 */
}

.menu {
  color: white;
  background-color: transparent;
  font-weight: normal;
  font-size: 1.8rem;
  margin: 3px 2px;
}

.principal {
  background-color: #a21010;
  padding: 10px;
  color: white;
  border-radius: 5px;
  width: 400px;
  font-size: 3rem;
  text-align: center;
}  

a {
  text-decoration: none;
  color: #553f75;
}

button {
  background-color: #553f75;
  color: white;
  font-size: 2.4rem;
  font-weight: bold;
  border-style: none;
  border-radius: 5px;
  padding: 3px 10px;
  margin: 3px 5px;
  min-width: 35px;
  cursor: pointer;
}

button:focus {
  outline: 0;
}

input[type='text'] {
  border-radius: 5px;
  font-size: 2.4rem;
  width: 100%;
  line-height: 4rem;
  padding: 3px;
}
</style>