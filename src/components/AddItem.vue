<template>
  <form class="form" 
        v-on:submit.prevent="onSubmit"
        v-bind:class="{active: fullWidth}"
  >
    <input class="form-elem" type="text" placeholder="I want..."
           @click="addFullWidth"
           v-model="title"><!-- v-model="title" запоминает значение строки -->
    <button class="form-elem" type="submit">
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
      <circle cx="12" cy="12" r="10"/>
      <line x1="12" y1="8" x2="12" y2="16"/>
      <line x1="8" y1="12" x2="16" y2="12"/>
    </svg>
    </button>
  </form>
</template>
<script>
export default {
  data() {
    return {
      title: '',
      fullWidth: false
    }
  },
  methods: {
    onSubmit() {
     console.log(this.title);
    //  если поле не пустое, создаем новый обьект
    // и передаем ключи id, title, completed
     if (this.title !== '') {  // или (this.title.trim())
       const newItem = {
         id: Date.now(),
         title: this.title,
         completed: false
       }
        this.$emit('add-item', newItem)
        this.title = ''
     }
    },
    addFullWidth() {
      this.fullWidth = true
    },
  }
}
</script>

<style>
.form {
  display: flex;
  margin-bottom: 30px;
  width: 100%;
}
.form .form-elem {
  border: none;
  border-radius: 4px;
  transition: .3s ease-in-out;
}
input.form-elem {
  width: 30%;
  padding: 15px;
  background: #fcfcfc;
}
input.form-elem::placeholder {
  font-family: "Mukta", Helvetica, Arial, sans-serif;
}
button.form-elem {
  background: #2c3e50;
  padding: 0 10px;
}
button.form-elem:hover {
  transform: scale(0.95);

}
form.active input.form-elem{
  width: 90%;
  background:#f3f3f3;
}
</style>