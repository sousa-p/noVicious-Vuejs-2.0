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
        v-for="(nota,i) in superacao.notas"
        :key="i"
        :nota="nota"
        @excluirNota="excluirNota(i)"
      />
      <button id="addNota" @click="showModalAddNota = true">Adicionar</button>
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
    this.superacao = this.superacoes[route.params.id]
  },
  watch: {
    $route: function (to, from) {
      this.superacao = this.superacoes[to.params.id]
    }
  },
  methods: {
    excluirNota (i) {
      this.superacao.notas.splice(i, 1)
    },
    addNota (mensagem) {
      const data = new Date()
      this.superacao.notas.push({
        data: `${String(data.getDate()).padStart(2, '0')}/${String(data.getMonth() + 1).padStart(2, '0')}/${data.getFullYear()}`,
        mensagem: mensagem
      })
    }
  }
}
</script>
