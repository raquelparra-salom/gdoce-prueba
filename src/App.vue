<template>
  <HeaderPage title="Juega con la máquina"/>
  <FormSearchNumber/>
</template>

<script>
import FormSearchNumber from './components/FormSearchNumber.vue'
import HeaderPage from './components/HeaderPage.vue'

export default {
  name: 'App',
  components: {
    FormSearchNumber,
    HeaderPage,
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
