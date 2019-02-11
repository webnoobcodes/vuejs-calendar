<template>
  <div id="app">
    <Calendar />
  </div>
</template>

<script>
  import Calendar from './components/Calendar.vue'
  
  export default {
    components: {
      Calendar
    }
  }
</script>

<style lang="scss">
  body {
    background-color: #493840;
    margin: 0;
    padding: 0;
  }

  #app {
    font-family: 'Avenir', Arial, Helvetica;
    font-size: 1.6rem;
    color: #333;

    display:flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100vh;
  }
</style>
