<template>
  <div class="wrapper_modal">
    <div class="modal">
      <div class="modal_header">
        <p>Nova Superação</p>
        <button class="modal_btn__fechar" @click="$emit('close')">
          <ion-icon name="close"></ion-icon>
        </button>
      </div>
      <form class="modal_form">
        <div class="form-group">
          <label>Superação:</label>
          <input class="input" type="text" v-model="nomeSuperacao" name="nomeSuperacao"/>
        </div>
        <div class="form-group">

          <label>Cor:</label>
          <div class="wrapper_colors">
            <div class="color" @click="setColor('#ff9400')" style="background-color: #ff9400;"></div>
            <div class="color" @click="setColor('#ffa500')" style="background-color: #ffa500;"></div>
            <div class="color" @click="setColor('#ffd700')" style="background-color: #ffd700;"></div>
            <div class="color" @click="setColor('#e3ff00')" style="background-color: #e3ff00;"></div>
            <div class="color" @click="setColor('#c1ff00')" style="background-color: #c1ff00;"></div>
            <div class="color" @click="setColor('#9eff00')" style="background-color: #9eff00;"></div>
            <div class="color" @click="setColor('#00ff8c')" style="background-color: #00ff8c;"></div>
            <div class="color" @click="setColor('#00ffc7')" style="background-color: #00ffc7;"></div>
            <div class="color" @click="setColor('#00ffed')" style="background-color: #00ffed;"></div>
            <div class="color" @click="setColor('#00c3ff')" style="background-color: #00c3ff;"></div>
            <div class="color" @click="setColor('#009bff')" style="background-color: #009bff;"></div>
            <div class="color" @click="setColor('#005eff')" style="background-color: #005eff;"></div>
            <div class="color" @click="setColor('#2900ff')" style="background-color: #2900ff;"></div>
            <div class="color" @click="setColor('#4a00ff')" style="background-color: #4a00ff;"></div>
            <div class="color" @click="setColor('#6700ff')" style="background-color: #6700ff;"></div>
          </div>
        </div>
        <button class="modal_form__btn" @click.prevent="addSuperacao(nomeSuperacao, corSuperacao); $emit('close')">Criar</button>
      </form>
    </div>
  </div>
</template>

<style lang="sass">
.wrapper_colors
  display: flex
  flex-wrap: wrap
  gap: 10px
  justify-content: space-between

  .color
    width: 50px
    height: 35px
    border-radius: 5px
    box-shadow: 0 0 5px #00000030
    cursor: pointer
  .selecionado
    outline: 3px dashed #ff000085 !important

.wrapper_modal
  width: 100%
  height: 100%
  z-index: 9999
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
    gap: 50px
    padding: 20px

    .form-group
      width: 100%
      display: flex
      gap: 25px
      flex-direction: column

    .modal_form__btn
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
      corSuperacao: '#000000',
      ultimoSelecionado: null
    }
  },

  methods: {
    setColor (color) {
      if (this.ultimoSelecionado) this.ultimoSelecionado.classList.remove('selecionado')
      event.target.classList.add('selecionado')
      this.ultimoSelecionado = event.target
      this.corSuperacao = color
    }
  }
}
</script>
