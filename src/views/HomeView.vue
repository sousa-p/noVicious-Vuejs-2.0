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
      <router-link :to="`/superacao/${i}`" class="superacao_card__nome">
        {{superacao.nome}}
      </router-link>
      <button @click="removeSuperacao(i)" class="superacao__remove">
        <ion-icon name="trash-bin"></ion-icon>
      </button>
    </div>
    <button class="btn__add" @click="$emit('showModalAddSuperacao')">Adicionar</button>
  </div>
</template>

<style lang="sass">
.wrapper
  gap: 30px

.superacao_card
  display: flex
  justify-content: space-between
  align-items: center
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

  .superacao_card__nome
    color: #000
    text-decoration: none
    font-size: 1.2em

.btn__add
  width: 175px
  height: 55px
  margin: 0 auto
  cursor: pointer
  padding: 20px 50px
  border: none
  border-radius: 5px
  background: #018040
  color: #fff
  font-weight: bolder
  text-transform: uppercase
  transition: .5s all linear

.btn__add:hover
  background: #016500

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
