# VueBaseWork
Работа с основными возможностями фреймворка Vue

Основные дерективы для манипуляция над элементами страницы:

 - v-show="view"
   - Добавляет/удаляет элемент в Dom (display: none/block)
 - v-if="visible"
   - Скрывает/показывает элемент (visible: visible/hidden)
 - v-model="..." 
   - Осуществялет render элемента (перерисовывает элемент)
 - v-on:click="..."
   - Вещает событие на элемент и вызввает переданную функцию
 - v-bind:title="msgTitle"
   - Связывает дерективны
 -  v-bind:class="[sizeToggle ? 'large' : '', {'rounded': isRounded}]"
   - Осуществляет проверку на true/false и исходя их этого вещает класс на элемент 
 - v-bind:style="styles"
   - Задает инлайновые стили элементу исходя из переданных значений
 - v-bind:disabled="disabled">
   - Задает атрибут disabled элементу исходя из переданных значений
 - v-on:click="show = !show"
   - Если возвращаем true - тогда вещаем класс и наоборот
 - v-if="show"
   - Показывает/скрывает элемент исходя что возвращает show
