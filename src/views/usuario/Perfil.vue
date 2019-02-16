<template>
    <v-layout text-xs-center align-start justify-center>
        <v-card class="elevation-6">
            <v-card-text>
                <div class="ma-2">
                    Nome e sobrenome
                </div>
                <img class="ma-2 fotoPerfil" :src="require(`@/assets/fotoUsuario.png`)">
                <div class="ma-2">
                    Descrição
                </div>
                <a href="" class="ma-2 link">Biografia</a>
            </v-card-text>
        </v-card>
    </v-layout>
</template>


<style>
    .fotoPerfil {
        width: 200px;
        height: 100%;
    }

    .link {
        text-decoration: none;
        font-size: 1rem;
        color: #553f75;
    }
</style>