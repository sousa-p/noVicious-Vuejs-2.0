<template>
  <div class="wrappper_modal">
    <button @click="$emit('close')">X</button>
    <form>
      <input type="text" v-model="mensagemNota"/>
      <button @click.prevent="addNota(mensagemNota); $emit('close')">Criar</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'ModalAddNota',
  props: ['addNota'],
  data () {
    return {
      mensagemNota: ''
    }
  }
}
</script>
