<template>
  <div class="todo-header">
    <input
      type="text" placeholder="請輸入你的任務名稱,按下確認鍵"
      v-model="title" @keyup.enter="addItem"
    />
  </div>
</template>
  
  <script>
export default {
  // 聲明接收屬性
  props: {
    // 屬性名稱:屬性類型
    addTodo: Function
  },
  data() {
    return {
      title: '',
    }
  },
  methods: {
    addItem() {
      // 1. 檢查參數值
      const title = this.title.trim()
      if (!title) { // 相當於title == ''
        alert('title參數為必填')
        return
      }
      // 2. 打包為todo對象
      const todo = { title, complete: false }
      // 3. 添加至集合物件中
      this.addTodo(todo)
      // 4. 復歸輸入框
      this.title = ''
    }
  }
}
  </script>
  
<style>
/* header */
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}
.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),
    0 0 8px rgba(82, 168, 236, 0.8);
}
</style>