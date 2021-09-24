<template>
  <div>
    <ul class="doings-list">

      <TodoItem
      v-for="(item, index) in doings"
      v-bind:item="item"
      v-bind:index="index"
      v-on:remove-item="removeItem"
      :key="item.id"
      />
<!--  если все выполнено -->
      <div v-if="!doings.length" class="message">
        Ooooooooooppss. <br>
        Congrats. You finished all doings!
      </div>
      <div v-else class="message">
        Soon there will be an assistant bot in this place..
      </div>
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'

export default {
  props:['doings'],
  index: Number,
  methods: {
    removeItem(id) {
      console.log(id);
      this.$emit('remove-item', id);
    },
  },
  components: {
    TodoItem
  }

}
</script>

<style scoped>
 ul.doings-list {
    margin-left: -40px;
}
 .message {
   margin-top: 30px;
   font-size: 20px;
   line-height: 110%;
 }
</style>