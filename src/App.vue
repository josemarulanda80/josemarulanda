<template >

  <TableCheckbox/>
</template>

<script>
import TableCheckbox from './components/TableCheckbox.vue'

export default {
  name: 'App',
  components: {
   
    TableCheckbox
  }
}
</script>

<style>
#app {
  -moz-osx-font-smoothing: grayscale;
  margin: auto;
  max-width:100%;
  padding: 4vh 2vh;
  text-align: center;
  color: #2c3e50;
  background: #2c3e50;
  height: 100vh;
  font-size: 3vh;
}

</style>
