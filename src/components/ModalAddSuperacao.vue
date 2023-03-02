<template>
  <div class="wrappper_modal">
    <button @click="$emit('close')">X</button>
    <form>
      <input type="text" v-model="nomeSuperacao"/>
      <button @click.prevent="addSuperacao(nomeSuperacao); $emit('close')">Criar</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'ModalAddSuperacao',
  props: ['addSuperacao'],
  data () {
    return {
      nomeSuperacao: ''
    }
  }
}
</script>
