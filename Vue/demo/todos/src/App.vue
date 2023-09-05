<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <!-- 使用標籤 TodoHeader / todo-header -->
      <TodoHeader :addTodo="addTodo" />
      <TodoList :todos="todos" :deleteTodoItem="deleteTodoItem" />
      <TodoFooter
        :todos="todos"
        :deleteCompleteTodos="deleteCompleteTodos"
        :selectAllTodosItem="selectAllTodosItem"
      />
    </div>
  </div>
</template>

<script>
// 宣告引入組件
import TodoHeader from './components/TodoHeader.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {

data() {
  return {
    // 透過localStorage讀取todos數據預設值為空集合物件
    todos: JSON.parse(window.localStorage.getItem('todos_key') || '[]')
  }
},
methods: {
  addTodo(todo) {
    this.todos.unshift(todo)
  },
  deleteTodoItem(index) {
    this.todos.splice(index, 1)
  },
  // 刪除所有已經完成的Todo項目
  deleteCompleteTodos() {
    this.todos = this.todos.filter(todo => !todo.complete)
  },
  // 修改完成狀態(全選或全不選)
  selectAllTodosItem(isComplete) {
    this.todos.forEach(todo => todo.complete = isComplete)
  }
},
watch: { // 監視
  todos: {
    deep: true, //深度監視
    handler: function (value) {
      //將最新的值,保存到localStorage
      window.localStorage.setItem('todos_key', JSON.stringify(value))
    }
  }
},
// 映射標籤
components: {
  TodoHeader, TodoList, TodoFooter
}
}
</script>

<style>
/* app */
.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
