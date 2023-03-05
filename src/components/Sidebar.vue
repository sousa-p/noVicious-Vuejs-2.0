<template>
  <div class="Sidebar">
    <p id="logo">No vicious</p>
    <p id="frase">
      XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
      XXXXXXXXXXXXXXXXXXXXXXXXX
      XXXXXXXX
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
  padding: 10px
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
</style>

<script>
export default {
  name: 'SidebarComponent',
  props: ['superacoes']
}
</script>
