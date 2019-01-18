<template>
  <div id="app">
    <h1>{{ message }}</h1> <!--Интерполяция для вывода данных переданных в объект massage-->
    <StartScreen /> <!--Экспорт компонента--> 
  </div>
</template>

<script>
  import StartScreen from './components/StartScreen.vue'

  export default {
    data () {
      return {
        message: 'Основы Vue'
      }
    },
   
  }
</script>

