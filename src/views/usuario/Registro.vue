<template>
  <v-layout justify-center align-center>
    <v-flex xs12 sm8 md6 lg5 xl4>
      <v-slide-y-transition mode="out-in">
        <v-card v-if="step == 1" :key="1" class="elevation-6">
          <v-toolbar color="primary" dark card>
            <v-toolbar-title>Criar conta</v-toolbar-title>
          </v-toolbar>
          <v-card-text>
            <v-text-field label="Email"></v-text-field>
            <v-text-field label="Senha" type="password"></v-text-field>
          </v-card-text>
          <v-card-text>
            <v-layout justify-end>
              <v-btn @click="step++" color="secondary">Seguinte</v-btn>
            </v-layout>
          </v-card-text>
        </v-card>
        <v-card v-if="step == 2" :key="2" class="elevation-6">
          <v-toolbar color="primary" dark card>
            <v-toolbar-title>Insira seu nome e sobrenome</v-toolbar-title>
          </v-toolbar>
          <v-card-text>
            <v-text-field label="Nome"></v-text-field>
            <v-text-field label="Sobrenome"></v-text-field>
          </v-card-text>
          <v-card-text>
            <v-layout justify-end>
              <v-btn @click="step++" color="secondary">Seguinte</v-btn>
            </v-layout>
          </v-card-text>
        </v-card>
        <v-card v-if="step == 3" :key="3" class="elevation-6">
          <v-toolbar color="primary" dark card>
            <v-toolbar-title>Insira a sua data de nascimento</v-toolbar-title>
          </v-toolbar>
          <v-card-text>
            <v-layout justify-center>
              <v-date-picker v-model="dataNascimento" reactive locale="pt-br" class="elevation-3"></v-date-picker>
            </v-layout>
          </v-card-text>
          <v-card-text>
            <v-layout justify-end>
              <v-btn color="secondary">Criar conta</v-btn>
            </v-layout>
          </v-card-text>
        </v-card>
      </v-slide-y-transition>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data() {
    return {
      step: 1,
      dataNascimento: null
    };
  }
};
</script>