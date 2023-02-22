<template>
  <ModalAddSuperacao
  v-if="showModalAddSuperacao"
  @close="showModalAddSuperacao = false"
  :addSuperacao="addSuperacao"
  />
  <header>
    <nav>
      <a href="#">NoVicious</a>
      <router-link to="/">Home</router-link> |
    </nav>
  </header>
  <main>
    <SidebarComponent
      @showModalAddSuperacao="showModalAddSuperacao = true"
      :superacoes="superacoes"
      :removeSuperacao="removeSuperacao"
    />
    <router-view
    :superacoes="superacoes"
    />
  </main>
  <footer>
    <p id="credito">Desenvolvido por Pedro S.</p>
  </footer>
</template>

<style lang="sass">
$header-footer-altura: 65px
$black: #212227
$shadow: 0px 0px 10px rgba(0,0,0,0.5)

*
  padding: 0
  margin: 0
  box-sizing: border-box
  color: $black
  font-family: 'Courier New', Courier, monospace

#app
  width: 100vw
  height: 100vh

header, main, footer
  width: 100%
  display: flex

header,footer
  height: $header-footer-altura
  align-items: center
  padding: 0 25px
  box-shadow: $shadow
  background: #4f6367

main
  background: #eef5fb
  height: calc(100% - $header-footer-altura*2)
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
    addSuperacao (nomeSuperacao) {
      this.superacoes.push({
        nome: nomeSuperacao,
        notas: [],
        superada: false
      })
    },
    removeSuperacao (i) {
      this.superacoes.splice(i, 1)
      this.$router.replace('/')
    }
  }
}
</script>
