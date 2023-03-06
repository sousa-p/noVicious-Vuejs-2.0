<template>
  <div class="nota">
    <div class="nota_header">
      <input type="date" name="data" id="data">
      <div class="data_nota-atual">
        <p id="ano">{{ nota.ano }}</p>
        <p id="mes">{{ nota.mes }}</p>
        <p id="dia">{{ nota.dia }}</p>
      </div>
    </div>
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
