<template>
  <div class="nota">
    <div class="nota_header">
      <div>
        <input type="date" name="data" id="data">
      </div>
      <div class="data_nota-atual">
        <p id="dia">{{ nota.dia.padStart(2, '0') }}</p>
        <p id="mes">{{ nota.mes.padStart(2, '0') }}</p>
        <p id="ano">{{ nota.ano }}</p>
      </div>
    </div>
    <div class="nota_content">
      <button v-if="nota.mensagem" @click="$emit('excluirNota')">
        <ion-icon name="trash-bin"></ion-icon>
      </button>
      <p v-if="nota.mensagem">{{ nota.mensagem }}</p>
      <p v-else>Não há notas. Que tal adicionar uma?</p>
    </div>
  </div>
</template>

<style lang="sass">
.nota_header
  display: flex
  justify-content: space-between

.data_nota-atual
  display: flex
  justify-content: space-between
  width: 280px
  gap: 15px

  p
    text-align: end
    color: #fff
    background: #12103f
    padding: 15px 10px

  #ano
    width: 50%
    border-radius: 30px 0 0 0

  #mes,
  #dia
    width: 33.33333%

.nota_content
  width: 50%
  height: 500px
  padding: 25px
  text-align: center
  margin: 30px auto
  border-radius: 5px
  box-shadow: 0 0 15px #00000015
  background-color: #fff
</style>

<script>
export default {
  name: 'NotaComponent',
  props: ['nota']
}
</script>
