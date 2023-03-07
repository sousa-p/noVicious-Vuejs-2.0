<template>
  <div class="Sidebar">
    <p id="logo">No vicious</p>
    <p id="frase">
      "{{ fraseMotivacional }}"
    </p>
    <div id="wrapper_superacoes">
      <p>
        {{
          superacoes.filter((superacao) => {superacao.superada}).length
        }} Superações
      </p>
    </div>
  </div>
</template>

<style lang="sass">
.Sidebar
  width: 25%
  padding: 25px
  min-width: 300px
  gap: 75px
  display: flex
  flex-direction: column
  justify-content: center
  align-items: center
  background: #12103f

.Sidebar p
  color: #fff

#logo
  font-weight: bold
  font-size: 1.6em

#frase
  display: flex
  align-items: center
  justify-content: center
  min-height: 100px
  line-height: 25px
  text-align: center

#wrapper_superacoes
  padding: 20px 50px
  border-radius: 15px
  background: rgba(255,255,255,0.1)
  backdrop: blur(5px)
  border: 1px solid rgba(255,255,255,0.2)

  p
    font-size: 1.1em

@media (max-width: 840px)
  .Sidebar
    width: 100%
    height: 200px
    gap: 0px
    justify-content: space-around

  #wrapper_superacoes
    padding: 15px 30px
</style>

<script>
import frases from '@/frases.json'
export default {
  name: 'SidebarComponent',
  props: ['superacoes'],
  data () {
    return {
      fraseMotivacional: frases[Math.floor(Math.random() * frases.length)].frase
    }
  }
}
</script>
