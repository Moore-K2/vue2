<template>
  <div class="myItem">
    <li>
      <label>
        <!-- checked与任务的done绑定 -->
        <input type="checkbox" :checked="todo.done" @click="check()" />
        <span>{{ todo.title }}</span>
      </label>
      <button class="btn btn-danger" @click="delTodo()">删除</button>
    </li>
  </div>
</template>

<script>
// 导出
export default {
  name: "MyItem",
  // 声明props接收来自Mylist组件的todo对象
  props: ["todo", "checkTodo", "deleteTodo"],
  methods: {
    // 勾选框操作时，获取todo对象的id,进而操作todo对象的done
    check() {
      // console.log(this.todo.id);
      this.checkTodo(this.todo.id);
    },
    delTodo() {
      if (confirm("你确定删除吗？")) {
        this.deleteTodo(this.todo.id);
      }
      // console.log(this.todo.id);
    },
  },
};
</script>

<style scoped>
/*  */
/*item*/
li:hover {
  background-color: #d4e5ee;
}
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
  border: 1px solid rgba(0, 0, 0, 0.1);
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
/* 鼠标指向父元素li上显示button */
li:hover button {
  display: block;
}
/* ?? */
li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
</style>