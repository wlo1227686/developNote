<template>
  <!-- 
onmouseenter : 進入該標籤時觸發
onmouseleave : 離開該標籤時觸發
onmouseover :  從子標籤進入標籤時觸發
onmouseout : 從標籤進入子標籤時觸發
   -->
  <li
    @mouseenter="handleShow(true)"
    @mouseleave="handleShow(false)"
    :style="{ background: bgColor }"
  >
    <label>
      <input type="checkbox" v-model="todo.complete" />
      <span>{{ todo.title }}</span>
    </label>
    <button class="btn btn-danger" v-show="isShow" @click="deleteItem">刪除</button>
  </li>
</template>
  
  <script>

export default {
  props: {
    // 屬性名稱:屬性類型
    todo: Object,
    index: Number,
    deleteTodoItem: Function
  },
  data() {
    return {
      bgColor: '#fff', // 默認背景顏色
      isShow: false // 刪除按鈕是否顯示
    }
  },
  methods: {
    handleShow(isEnter) {
      if (isEnter) {
        this.bgColor = '#eee'
        this.isShow = true
      } else {
        this.bgColor = '#fff'
        this.isShow = false
      }
    },
    deleteItem() {
      const { todo, index, deleteTodoItem } = this
      if (window.confirm(`確認刪除${todo.title}嗎?`)) {
        deleteTodoItem(index)
      }
    }
  }
}
  </script>
  
<style>
/* Item */
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}
li label {
  float: left;
  cursor: pointer;
}
li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}
li button {
  float: right;
  display: none;
  margin-top: 3px;
}
li:before {
  content: initial;
}
li:last-child {
  border-bottom: none;
}
</style>