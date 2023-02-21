<template>
  <div class="nota">
    <h1>{{ nota.data }}</h1>
    <p>{{ nota.mensagem }}</p>
    <button @click="$emit('excluirNota')">X</button>
  </div>
</template>

<script>
export default {
  name: 'NotaComponent',
  props: ['nota']
}
</script>
