<template>
  <ModalAddSuperacao
  v-if="showModalAddSuperacao"
  @close="showModalAddSuperacao = false"
  :addSuperacao="addSuperacao"
  />
  <main>
    <SidebarComponent
      :superacoes="superacoes"
    />
    <router-view
      @showModalAddSuperacao="showModalAddSuperacao = true"
      :superacoes="superacoes"
      :removeSuperacao="removeSuperacao"
    />
  </main>
</template>

<style lang="sass">
$header-footer-altura: 65px
$black: #212227
$shadow: 0px 0px 10px rgba(0,0,0,0.5)

*
  padding: 0
  margin: 0
  box-sizing: border-box
  font-family: 'Courier New', Courier, monospace

ion-icon
  font-size: 1.2em
  transition: .25s all linear

ion-icon:hover
  color: #99ffff

#app
  width: 100vw
  height: 100vh
  color: $black

main
  background: #eef5fb
  height: 100%
  display: flex

.wrapper
  width: 100%
  padding: 2.5% 2.5% 0 2.5%
  display: flex
  flex-direction: column

@media (max-width: 840px)
  h1
    text-align: center
  main
    display: block
</style>

<script>
import SidebarComponent from '@/components/Sidebar.vue'
import ModalAddSuperacao from '@/components/ModalAddSuperacao.vue'
export default {
  components: {
    SidebarComponent,
    ModalAddSuperacao
  },
  data () {
    return {
      superacoes: (localStorage.getItem('superacoes')) ? JSON.parse(localStorage.getItem('superacoes')) : [],
      showModalAddSuperacao: false
    }
  },
  watch: {
    superacoes: {
      handler (to) {
        localStorage.setItem('superacoes', JSON.stringify(to))
      },
      deep: true
    }
  },
  methods: {
    addSuperacao (nomeSuperacao, corSuperacao) {
      this.superacoes.push({
        nome: nomeSuperacao,
        notas: [],
        superada: false,
        cor: corSuperacao
      })
    },
    removeSuperacao (i) {
      this.superacoes.splice(i, 1)
      this.$router.replace('/')
    }
  }
}
</script>
