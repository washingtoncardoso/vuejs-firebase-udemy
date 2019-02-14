<template>
    <div>    
        <anuncio />
        <cliente :email="email" @onMudarEmail="atualizarEmail" />  
        <boletos />
        <email :emailRecebido="email" @onMudarEmail="atualizarEmail"/>
        <firma />   
     
    </div>
</template>





<script>

import Cliente from '@/components/Cliente.vue'
import Anuncio from '@/components/Anuncio.vue'
import Boletos from '@/components/Boletos.vue'
import Firma from '@/components/Firma.vue'
import Email from '@/components/Email.vue'

export default {
    components: { Anuncio, Cliente, Boletos, Firma, Email },
    data() {
        return {
            email: ''
        }
    },
    methods: {
        atualizarEmail(email) {
            this.email = email
        }
    }
}
</script>


<style>

.seccion {
  font-size: 2.4rem;
  color: #202020;
  background-color: #e9e9e9;
  border-radius: 5px;
  margin: 10px;
  padding: 1px;
}
.atributo {
    margin: 10px;
}
    
</style>



