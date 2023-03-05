<template>
  <div class="wrapper_modal">
    <div class="modal">
      <div class="modal_header">
        <p>Nova Superação</p>
        <button class="modal_btn__fechar" @click="$emit('close')">X</button>
      </div>
      <form class="modal_form">
        <label>Superação:</label>
        <input class="input" type="text" v-model="nomeSuperacao" name="nomeSuperacao"/>
        <label>Cor:</label>
        <input class="input" type="color" v-model="corSuperacao" name="corSuperacao"/>
        <button id="btn_add-superacao" @click.prevent="addSuperacao(nomeSuperacao, corSuperacao); $emit('close')">Criar</button>
      </form>
    </div>
  </div>
</template>

<style lang="sass">
.wrapper_modal
  width: 100%
  height: 100%
  display: flex
  justify-content: center
  align-items: center
  flex-direction: column
  position: absolute
  backdrop-filter: blur(5px)
  -webkit-backdrop-filter: blur(5px)
  background-color: #00000075

  button
    cursor: pointer

.modal
  width: 380px
  height: 530px
  display: flex
  justify-content: space-between
  align-items: center
  flex-direction: column
  border-radius: 7px
  background-color: #fff

  .modal_header
    width: 100%
    height: 10%
    display: flex
    justify-content: space-between
    align-items: center
    color: #fff
    padding: 0 20px
    border-radius: 7px 7px 0px 0px
    background-color: #12103f

    p
      font-size: 1.2em
      font-weight: bold
    .modal_btn__fechar
      color: #fff
      background: transparent
      border: none

  .modal_form
    width: 100%
    height: 90%
    display: flex
    flex-direction: column
    gap: 15px
    padding: 20px

    #btn_add-superacao
      width: 55.555%
      height: 60px
      background-color: #12103f
      border: none
      border-radius: 7px
      font-weight: bold
      color: #fff
      text-transform: uppercase
      align-self: center
</style>

<script>
export default {
  name: 'ModalAddSuperacao',
  props: ['addSuperacao'],
  data () {
    return {
      nomeSuperacao: '',
      corSuperacao: '#000000'
    }
  }
}
</script>
