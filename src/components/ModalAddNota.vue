<template>
  <div class="wrapper_modal">
    <div class="modal">
      <div class="modal_header">
        <p>Nota</p>
        <button class="modal_btn__fechar" @click="$emit('close')">X</button>
      </div>
      <form class="modal_form">
        <label for="mensagemNota">Digite sua nota:</label>
        <textarea type="text" v-model="mensagemNota" id="mensagemNota" name="mensagemNota"></textarea>
        <button class="modal_form__btn" @click.prevent="addNota(mensagemNota); $emit('close')">Criar</button>
      </form>
    </div>
  </div>
</template>

<style lang="sass">
.wrapper_modal
  left: 0
  top: 0

  #mensagemNota
    height: 75%
    resize: none

</style>

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
