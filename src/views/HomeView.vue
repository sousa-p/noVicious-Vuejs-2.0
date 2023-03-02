<template>
  <div class="wrapper">
    <h1>Home</h1>
    <p
    v-if="superacoes.length === 0"
    >
      Não há superações. Que tal começar a mudar sua vida?
    </p>
    <button @click="$emit('showModalAddSuperacao')">Add Superacao</button>
    <div
      v-for="(superacao, i) in superacoes"
      :key="i"
    >
      <router-link :to="`/superacao/${i}`">{{superacao.nome}}</router-link>
      <button @click="removeSuperacao(i)">X</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  props: ['superacoes', 'removeSuperacao']
}
</script>
