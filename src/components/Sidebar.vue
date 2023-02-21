<template>
  <div class="Sidebar">
    <button @click="addSuperacao; $emit('addSuperacao')">Add Superacao</button>
    <router-link
    v-for="(superacao, i) in superacoes"
    :key="i"
    :to="`/superacao/${i}`"
    >
      <p>{{superacao.nome}}</p>
    </router-link>
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
  props: ['superacoes']
}
</script>
