<template>
    <div class="seccion">
        <div class="atributo">
            <input v-model="email" @keyup.enter="atualizarEmail" type="text">
        </div>       
    </div>
</template>


<script>
export default {
    props: ['emailRecebido'],
    data() {
        return {
            email: ''
        }
    },
    methods: {
        atualizarEmail(event) {   
            this.$emit('onMudarEmail', this.email); 
        }
    },
    watch: {
        emailRecebido() {
            this.email = this.emailRecebido;
        }
    }
}
</script>

<style>

.email {
    text-align: left;
}
    
</style>