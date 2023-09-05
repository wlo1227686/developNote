<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" v-model="isAllComplete" />
    </label>
    <span>
      <span>已經完成 {{ completeSize }}</span> / 全部 {{ todos.length }}
    </span>
    <button
      class="btn btn-danger"
      v-show="completeSize"
      @click="deleteCompleteTodos"
    >
      清除已完成任務
    </button>
  </div>
</template>

<script>
export default {
  props: {
    // 屬性名稱:屬性類型
    todos: Array,
    deleteCompleteTodos: Function,
    selectAllTodosItem: Function
  },
  computed: {
    completeSize() {
      return this.todos.reduce((preTotal, todo) => preTotal + (todo.complete ? 1 : 0), 0)
    },
    isAllComplete: {
      get() { return this.completeSize == this.todos.length && this.todos.length != 0 },
      set(value) { this.selectAllTodosItem(value) } // value是當前checkbox最新的值
    }

  }
}
</script>
  
<style>
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}
.todo-footer label {
  display: inline-block;
  margin-right: 20px;
}
.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}
.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>