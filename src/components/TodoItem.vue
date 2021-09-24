<template>
  <li class="item" v-bind:class="{done:item.completed }">
    <div>
      <button class="btn-finish"
      v-on:click="finishItem"><!--  или можно так @click="item.completed = true"-->

        <span class="btn-text">Finish</span>
        <span class="btn-done-icon">
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" id="Layer_1" x="0px" y="0px" viewBox="100 67 315 390" xml:space="preserve" width="35" height="20" fill="#00af15">
          <g>
            <polygon class="st0" points="162.92,369.45 40.74,247.26 0,288 162.92,450.89 512,101.81 471.26,61.11  "/>
          </g>
          </svg>
        </span>
        </button>
      <span class="item-id"><b>{{ index + 1}}</b></span>
    </div>
    <span class="item-title"> {{ item.title }}</span>
    <button class="btn-close"
    v-on:click="$emit('remove-item', item.id)">

      <svg xmlns="http://www.w3.org/2000/svg" id="Layer_1" width="20" height="20" fill="#2c3e50" data-name="Layer 1" viewBox="1 0 105.16 122.88">
        <path class="cls-1" d="M11.17,37.16H94.65a8.4,8.4,0,0,1,2,.16,5.93,5.93,0,0,1,2.88,1.56,5.43,5.43,0,0,1,1.64,3.34,7.65,7.65,0,0,1-.06,1.44L94,117.31v0l0,.13,0,.28v0a7.06,7.06,0,0,1-.2.9v0l0,.06v0a5.89,5.89,0,0,1-5.47,4.07H17.32a6.17,6.17,0,0,1-1.25-.19,6.17,6.17,0,0,1-1.16-.48h0a6.18,6.18,0,0,1-3.08-4.88l-7-73.49a7.69,7.69,0,0,1-.06-1.66,5.37,5.37,0,0,1,1.63-3.29,6,6,0,0,1,3-1.58,8.94,8.94,0,0,1,1.79-.13ZM5.65,8.8H37.12V6h0a2.44,2.44,0,0,1,0-.27,6,6,0,0,1,1.76-4h0A6,6,0,0,1,43.09,0H62.46l.3,0a6,6,0,0,1,5.7,6V6h0V8.8h32l.39,0a4.7,4.7,0,0,1,4.31,4.43c0,.18,0,.32,0,.5v9.86a2.59,2.59,0,0,1-2.59,2.59H2.59A2.59,2.59,0,0,1,0,23.62V13.53H0a1.56,1.56,0,0,1,0-.31v0A4.72,4.72,0,0,1,3.88,8.88,10.4,10.4,0,0,1,5.65,8.8Zm42.1,52.7a4.77,4.77,0,0,1,9.49,0v37a4.77,4.77,0,0,1-9.49,0v-37Zm23.73-.2a4.58,4.58,0,0,1,5-4.06,4.47,4.47,0,0,1,4.51,4.46l-2,37a4.57,4.57,0,0,1-5,4.06,4.47,4.47,0,0,1-4.51-4.46l2-37ZM25,61.7a4.46,4.46,0,0,1,4.5-4.46,4.58,4.58,0,0,1,5,4.06l2,37a4.47,4.47,0,0,1-4.51,4.46,4.57,4.57,0,0,1-5-4.06l-2-37Z"/></svg>

    </button>
  </li>
</template> 

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true
    },
    index: Number
  },
  methods: {
    finishItem() {
      this.item.completed = true;
    }
  }
}
</script>

<style scoped>
 
  li.item {
    display: flex;
    align-items: stretch;
    justify-content: space-between;
    text-align: left;
    margin: 10px 0 10px 0;
    background: #f7f7f7;
    color: #000;
    border-radius: 5px;
}
  li.item div {
    display: flex;
  }
  span.item-id {
    display: flex;
    margin: 0 20px;
    align-items: center;
}
span.item-title {
  display: flex;
  align-items: center;
  font-size: 22px;
  word-break: break-all;
  width: 100%;
  line-height: 120%;
  padding: 10px 20px 10px 5px;
}
button {
  border: none;
  transition: .2s ease-in-out;
}
button:hover {
  transform: scale(0.95);
  background: #f7f7f7;

}
button.btn-close {
  padding: 17px 20px;
  border-top-right-radius: 4px;
  border-bottom-right-radius: 4px;
}
button.btn-finish {
    font-size: 16px;
    padding: 24px;
  border-top-left-radius: 4px;
  border-bottom-left-radius: 4px;
}

.btn-done-icon {
  display: none;
}
li.item.done .btn-done-icon {
  display: block;
}
li.item.done .btn-text {
  display: none;
}
li.item.done span {
  text-decoration: line-through;
  opacity: 0.6;
}
li.item.done {
    background: #3eaf55;
}
li.item.done .btn-finish:hover {
  transform: scale(1);
}
li.item.done .btn-finish {
  padding: 22px 27px;
}
li.item.done button.btn-close:hover {
  transform: scale(1) translateX(5px);
}

@media(max-width: 770px) {
  span.item-title {
    font-size: 15px;
  }
  button.btn-finish {
    padding: 13px;
    font-size: 13px;
  }
  span.item-id {
    margin: 0 10px;
  }
  li.item.done .btn-finish {
    padding: 13px;
  }
}
</style>