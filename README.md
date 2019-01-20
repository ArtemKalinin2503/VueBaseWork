# VueBaseWork
Работа с основными возможностями фреймворка Vue

Основные дерективы для манипуляция над элементами страницы:

 - v-show="view"
   - Показывает/скрывает элемент в Dom (display: none/block)
   export default {
    data() {
       view: false
    }
   }
