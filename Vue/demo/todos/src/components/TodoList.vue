<template>
  <ul class="todo-main">
    <!-- 使用標籤 -->
    <TodoListItem
      v-for="(todo, index) in todos"
      :key="index"
      :todo="todo"
      :index="index"
      :deleteTodoItem="deleteTodoItem"
    />
  </ul>
</template>
  
<script>
// 宣告載入組件(TodoListItem)
import TodoListItem from './TodoListItem.vue'

export default {
  // 聲明接收屬性
  props: {
    // 屬性名稱:屬性類型
    todos: Array,
    deleteTodoItem: Function
  },
  // 映射標籤
  components: { TodoListItem }
}
</script>
  
<style>
/* List */
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}
.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>