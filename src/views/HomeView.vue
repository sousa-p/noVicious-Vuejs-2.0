<template>
  <div class="wrapper">
    <h1>Home</h1>
    <p
    v-if="superacoes.length === 0"
    >
      Não há superações. Que tal começar a mudar sua vida?
    </p>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  props: ['superacoes']
}
</script>
