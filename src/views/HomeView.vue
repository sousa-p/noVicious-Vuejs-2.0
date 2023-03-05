<template>
  <div class="wrapper">
    <h1>Home</h1>
    <p
    v-if="superacoes.length === 0"
    >
      Não há superações. Que tal começar a mudar sua vida?
    </p>
    <div class="superacao_card" :style="`border-left-color: ${superacao.cor}`"
      v-for="(superacao, i) in superacoes"
      :key="i"
    >
      <router-link :to="`/superacao/${i}`" class="superacao_card__nome">{{superacao.nome}}</router-link>
      <button @click="removeSuperacao(i)" class="superacao__remove">X</button>
    </div>
    <button id="btn__superacao" @click="$emit('showModalAddSuperacao')">Adicionar</button>
  </div>
</template>

<style lang="sass">
.wrapper
  gap: 30px

.superacao_card
  display: flex
  justify-content: space-between
  margin: 0 auto
  flex-direction: row
  padding: 15px 25px
  border-radius: 5px
  box-shadow: 0 0 5px rgba(0,0,0,0.1)
  background: #fff
  width: 100%
  height: 75px
  border-left-width: 15px
  border-left-style: solid

#btn__superacao
  width: 175px
  height: 55px
  margin: 0 auto
  cursor: pointer
  padding: 20px 50px
  border: none
  border-radius: 5px
  background: green
  color: #fff
  font-weight: bolder
  text-transform: uppercase

.superacao__remove
  cursor: pointer
  background: transparent
  border: none
</style>

<script>
export default {
  name: 'HomeView',
  props: ['superacoes', 'removeSuperacao']
}
</script>
