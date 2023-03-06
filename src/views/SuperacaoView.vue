<template>
  <div class="wrapper">
    <ModalAddNota
    v-if="showModalAddNota"
    :addNota="addNota"
    @close="showModalAddNota = false"
    />
    <div class="superacao">
      <div class="header_superacao">
        <h1>{{ superacao.nome }}</h1>
        <router-link :to="`/`">Voltar</router-link>
      </div>
      <p
        v-if="superacao.notas.length === 0"
      >
        Não há notas nesta superação. Que tal começar com uma?
      </p>
      <NotaComponent
        v-else
        :key="idUltimaNota"
        :nota="notaAtual"
        @excluirNota="excluirNota(idUltimaNota)"
      />
      <button class="btn__add" @click="showModalAddNota = true">Adicionar</button>
    </div>
  </div>
</template>

<style lang="sass">
.superacao
  width: 100%
  max-height: 100%
  overflow: auto
  display: flex
  flex-direction: column

</style>

<script>
import { useRoute } from 'vue-router'
import NotaComponent from '@/components/Nota.vue'
import ModalAddNota from '@/components/ModalAddNota.vue'
export default {
  name: 'SuperacaoView',
  components: {
    NotaComponent,
    ModalAddNota
  },
  data () {
    return {
      showModalAddNota: false
    }
  },
  props: ['superacoes'],
  created () {
    const route = useRoute()
    const idSuperacao = route.params.id
    this.superacao = this.superacoes[idSuperacao]
    this.idUltimaNota = this.superacoes[idSuperacao].notas.length - 1
    this.notaAtual = this.notaAtual = this.superacoes[idSuperacao].notas[this.idUltimaNota]
  },
  watch: {
    $route: function (to, from) {
      const idSuperacao = to.params.id
      this.superacao = this.superacoes[idSuperacao]
      this.idUltimaNota = this.superacoes[idSuperacao].notas.length - 1
      this.notaAtual = this.superacoes[idSuperacao].notas[this.idUltimaNota]
    },
    superacoes: {
      handler (to) {
        this.idUltimaNota = this.superacao.notas.length - 1
        this.notaAtual = this.superacao.notas[this.idUltimaNota]
      },
      deep: true
    }
  },
  methods: {
    excluirNota (i) {
      this.superacao.notas.splice(i, 1)
    },
    addNota (mensagem) {
      const data = new Date()
      this.superacao.notas.push({
        ano: String(data.getFullYear()),
        mes: String(data.getMonth() + 1),
        dia: String(data.getDate()),
        mensagem: mensagem
      })
    }
  }
}
</script>
