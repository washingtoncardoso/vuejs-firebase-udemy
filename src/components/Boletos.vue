<template>
  <div>
    <div class="seccion">
      <div
        v-if="!pago && boletos == 0"
        class="mensagem informacao"
      >Selecione pelo menos um ingresso.</div>
      <div v-else-if="!pago && boletos > 0" class="mensagem advertencia">Complete sua compra.</div>
      <div v-else class="mensagem exito">Bem Vindo!</div>
      <div class="atributo">
        <span>Assentos</span>
      </div>
      <div class="atributo">
        <button
          @click="selecionar(assento, index)"
          v-for="(assento, index) in assentos"
          :key="index"
        >{{ assento }}</button>
      </div>
    </div>
    <div class="seccion">
      <div class="atributo">
        <span>Boletos</span>
      </div>
      <div class="atributo">
        <span class="boletos">{{ boletos }}</span>
      </div>
      <div v-show="boletos > 0" class="atributo">
        <span>Total: ${{ total }}</span>
      </div>
      <div class="atributo">
        <button
          class="selecao"
          @click="remover(assento, index)"
          v-for="(assento, index) in selecionados"
          :key="index"
        >{{ assento }}</button>
      </div>
      <!--        
            <div class="atributo">            
                <button @click="atualizarQtde(-1)">-</button>
                <button @click="atualizarQtde(1)">+</button>
            </div>
      -->
      <div v-if="!pago && boletos > 0" class="atributo">
        <button @click="pago = true">Pagar</button>
      </div>
      <div v-if="pago" class="atributo">
        <button @click="reiniciar">Reiniciar</button>
      </div>
      <div class="atributo">
        <span class="comissao" :class="classComissao">${{ comissao }}</span>
      </div>
    </div>
    <transition name="fade">
      <tiquete v-if="pago">
        <div slot="obra">
          <span>Rei Leão</span>
        </div>
        <div slot="horario">
          <span>2019-05-24 22:00</span>
        </div>
        <div slot="assentos">
          <span class="assento" v-for="(assento, index) in selecionados" :key="index">{{ assento }}</span>
        </div>
        <div slot="total">
          <span>{{ total }}</span>
        </div>
      </tiquete>
    </transition>
  </div>
</template>




<script>
import Tiquete from "./Tiquete";

export default {
  components: { Tiquete },
  data() {
    return {
      //boletos: 0,
      comissao: 0,
      classComissao: "neutro",
      pago: false,
      assentos: ["A1", "A2", "A3", "A4", "A5", "B1", "B2", "B3", "B4", "B5"],
      selecionados: []
    };
  },
  computed: {
    boletos() {
      return this.selecionados.length;
    },
    total() {
      return this.boletos * 100;
    }
  },
  methods: {
    remover(assento, index) {
      if (this.pago) {
        return;
      }
      this.selecionados.splice(index, 1);
      this.assentos.push(assento);
      this.assentos.sort();
    },
    selecionar(assento, index) {
      if (this.pago) {
        return;
      }
      this.assentos.splice(index, 1);
      this.selecionados.push(assento);
      this.selecionados.sort();
    },
    /*atualizarQtde(qtde) {
            this.boletos += qtde;

            if (this.boletos > 10) {
                this.boletos = 10;
            } else if (this.boletos < 0) {
                this.boletos = 0;
            }
        },*/
    reiniciar() {
      this.pago = false;
      //this.boletos = 0;
      this.comissao = 0;
      this.assentos.push(...this.selecionados);
      this.assentos.sort();
      this.selecionados = [];
    }
  },
  watch: {
    boletos(newValue, oldValue) {
      if (newValue > oldValue) {
        this.comissao += 10;
      } else {
        this.comissao -= 15;
      }

      if (this.comissao < 0) {
        this.comissao = 0;
      }
    },
    comissao(newValue, oldValue) {
      if (this.comissao == 0) {
        this.classComissao = "neutro";
      } else if (newValue > oldValue) {
        this.classComissao = "increment";
      } else {
        this.classComissao = "decrement";
      }
    }
  }
};
</script>

<style>
.assento {
  font-size: 1.8rem;
  padding: 3px;
  margin: 3px;
  border-style: solid;
  border-color: black;
  border-width: 1px;
}

.boletos {
  font-size: 4rem;
  font-weight: bold;
}

.comissao {
  font-size: 3.2rem;
}

.neutro {
  color: black;
}

.increment {
  color: green;
}

.decrement {
  color: red;
}

.mensagem {
  border-radius: 5px;
  border-width: 4px;
  border-style: dashed;
  padding: 10px;
  font-size: 2.1rem;
  font-weight: bold;
}

.informacao {
  border-color: blue;
}

.advertencia {
  border-color: orange;
}

.exito {
  border-color: green;
}

.selecao {
  background-color: green;
}
</style>