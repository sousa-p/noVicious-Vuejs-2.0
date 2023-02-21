<template>
  <div class="Sidebar">
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

<style lang="sass" scoped>
.Sidebar
  width: 20%
  background: #7a9e9f
</style>

<script>
export default {
  name: 'SidebarComponent',
  props: ['superacoes', 'removeSuperacao']
}
</script>
