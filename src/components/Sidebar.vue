<template>
  <div class="Sidebar">
    <p id="logo">No vicious</p>
    <p>
      XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
      XXXXXXXXXXXXXXXXXXXXXXXXX
      XXXXXXXX
    </p>
    <div>
      <p>
        {{
          superacoes.filter((superacao) => {superacao.superada}).length
        }} Superações
      </p>
    </div>
  </div>
</template>

<style lang="sass">
.Sidebar
  width: 22.5%
  background: #12103f

p
  color: #fff
</style>

<script>
export default {
  name: 'SidebarComponent',
  props: ['superacoes']
}
</script>
