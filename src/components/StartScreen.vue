<template>
  <div class="wrapper-StartScreen-Component">
      <h1>Компонент StartScreen!</h1>
      <div v-show="view" class="red-block"></div>
      <div v-if="visible" class="green-block"></div>
      <div class="directive-v-model-block">
        <input type="text" v-model="valueInput" />
        <p> {{ valueInput }}</p>
        <input type="checkbox" v-model="checked" />
        <label for="checkbox">{{ checked }}</label>
      </div>
      <div class="dirictive-event-dom">
        <p>Увеличиваем значение: {{ count }}</p>
        <button v-on:click="countUp">+1</button>
      </div>
      <div class="dirictive-event-dom">
        <a>{{ cleanUrl }}</a>
        <input type="text" v-model="url"/>
        <button v-on:click="cleanerUrl">Clean URL</button>
      </div>
      <div class="dirictive-v-bind">
        <h3 v-bind:title="msgTitle">Заголовок с атрибутом title (навидите на него)</h3>
      </div>
       <div class="dirictive-v-bind-class">
         <button v-bind:class="[sizeToggle ? 'large' : '', {'rounded': isRounded}]"
                 v-bind:style="styles"
                 v-bind:disabled="disabled">
           Start
         </button>
         <ul>
           <li>
             <label for="">Увеличить шрифт</label>
             <input type="checkbox" v-model="sizeToggle" />
           </li>
           <li>
             <label for="">Изменить цвет</label>
             <input type="checkbox" v-model="isRounded" />  
           </li>   
           <li>
             <label for="">Disable</label>
             <input type="checkbox" v-model="disabled" />
           </li>
           <li>
             <input type="text" v-model="fontColor"/>
           </li>
           <li>   
             <input type="text" v-model="backgroundColor"/>
           <li/>
         </ul>
      </div>
      <div class="vue-animation">
        <h5>Блок с анимацией</h5>
        <!--С помощью дерективы v-on:click - будем изменять show-->
        <button v-on:click="show = !show">Toggle</button>
        <!--Тег для анимации все что внутри данного тега будет применяться анимация-->
        <transition name="fade">
          <!--Если деректива v-if - будет возвращать false - тогда элемент будет скрыт-->
          <p v-if="show">Lorem ipsun dolor sit amet!</p>
        </transition>
        <transition name="newAnim">
          <div class="box" v-if="show"></div>
        </transition>
      </div>
  </div>
</template>

<script>
  export default {
    data () {
     return {
       view: false,     //Деректива v-show - показывает/скрывает элемент (просто display: none) в dom (просто передаем ее true/false) 
       visible: true,   //Деректива v-if - удаляет или вставляет элемент в dom дерево (в отличие от дерективы v-show которая просто скрывает элемент)
       valueInput: '',  //Деректива v-model - Изменяет dom мгновенно делая render (изменение/вывод)
       checked: 'true', //Деректива v-model - в данном случае денамически изменяет значение  label (true/false)
       count: 0,        //Деректива v-on:click - создает передеданое в нее событие (в данном случае countUp)
       url: '',         //Деректима v-model - в данном случае будет в данный объект записывать значение input
       cleanUrl: '',    //Деректива v-on:click - в данном случае будет записывать в данный объект значение объекта url и с помощью регулярного выражение обрезать его
       msgTitle: 'Атрибут title', //Деректива v-bind - связывает дерективы (в данном случае с помощью данной дерективы создали атрибут title  для заголовка и передали туда значение объекта msgTitle)
       sizeToggle: false, //Деректива v-bind:class - делает проверку на переданные условия (в данном случае если sizeToggle возвращает true тогда применить класс large), объект sizeToggle измененяем с помощью дерективы v-model переданной в  input type="checkbox"
       isRounded: false,  //Деректива v-bind:class  - в данном случае будет проверять значение объекта isRounded, если оно true, тогда добавиться класс rounded кнопке выше
       disabled: false,   //Деректива v-bind - в данном случае проверит объект disabled и если оно вернет true, кнопке выше добавиться атрибут disabled="disabled"
       fontColor: '#ccc', //Деректива v-bind:style - добавляет атрибут style в данном случае кнопке и добавляет стили которые мы прописали в input c дерективой v-model="fontColor"
       backgroundColor: 'yellow', //Деректива v-bind:style - добавляет атрибут style в данном случае кнопке и добавляет стили которые мы прописали в input c дерективой v-model="backgroundColor"
       show: false      //Деректива v-if - изменяет значение show (true/false), если show - то элемент показывается и наоборот
      }
    },
    methods: {
      countUp: function() { //В методах опишем событие countUp которое мы передали с помощью дерективы v-on:click
        this.count += 1     //Увеличем значение count (описанное выше) и увеличемна 1
      },
      cleanerUrl: function() {
        this.cleanUrl = this.url.replace(/^https?:\/\//, '').replace(/\/$/,'')
      }
    },
    computed: {
      styles: function() {
        return {
          color: this.fontColor,
          background: this.backgroundColor
        }
      }
    }
  }
</script>

//Стили только для данного компонента scoped (значит только для этого компонента)
<style scoped>
 .wrapper-StartScreen-Component {
   max-width: 1200px;
   margin: 20px auto;
   padding: 20px;
   background: whitesmoke;
   border-radius: 5px;
   border: 1px solod silver
 }
 .red-block {
   width: 50px;
   height: 50px;
   background: red;
 }
 .green-block {
   width: 50px;
   height: 50px;
   background: green;
 }
 .directive-v-model-block {
   padding: 10px;
   border: 1px solid silver;
   margin-top: 10px;
   width: 300px;
 }
 .dirictive-event-dom {
   border: 1px solid silver;
   margin-top: 10px;
   padding: 10px;
   width: 300px;
 }
 .dirictive-v-bind {
   border: 1px solid silver;
   margin-top: 10px;
   padding: 10px;
   width: 300px;
 }
 .dirictive-v-bind-class {
   border: 1px solid silver;
   margin-top: 10px;
   padding: 10px;
   width: 300px;
 }
 .large {
     font-size: 50px;
 }
 .rounded {
   background: red;
 }
 .vue-animation {
   border: 1px solid silver;
   margin-top: 10px;
   padding: 10px;
   width: 300px;
 }
 /* Стили для анимации */
 .fade-enter-active, .fade-leave-active {
   transition: opacity .5s;
 }
 .fade-enter, .fade-leave-to {
   opacity: 0;
 }
 .box {
   width: 100px;
   height: 100px;
   background: orange;
 }
 /* Стили для анимации */
 .newAnim-enter-active {
   animation: newAnim-in .5s;
 }
 .newAnim-leave-active {
   animation: newAniw-in .5s reverse;
 }
 @keyframes newAnim-in {
   0% {
     transform: scale(0);
   }
   50% {
     transform: scale(1.5);
   }
   100% {
     transform: scale(1);
   }
 }


</style>


