<template>
  <div class="todo-header">
    <div class="title">
      <h2 style="text-align: center; color: red">Todo List</h2>
    </div>
    <input
      type="text"
      placeholder="请输入你的任务名称，按回车键确认"
      v-model="title"
      @keyup.enter="add()"
    />
  </div>
</template>

<script>
// 引入nanoid函数
import { nanoid } from "nanoid";
export default {
  name: "TopHeader",
  data() {
    return {
      //输入框输入的值
      title: "",
    };
  },
  methods: {
    // add1(event) {
    //   console.log(event.target.value);
    // },
    add() {
      // console.log(this.title);
      if (!this.title.trim()) return alert("不能输入为空");
      // 将一个用户的输入包装成一个todo对象
      const todoObj = { id: nanoid(), title: this.title, done: false };
      // console.log(todoObj);
      //现在是要将todo对象添加到MyItem，但现在还不能实现兄弟之间传值，所以要把todolist放入APP父组件
      // 调用App父组件的方法
      // this.addTodo(todoObj);
      this.$emit("addTodoEvent", todoObj);
      this.title = "";
    },
  },
  // 接收来自父组件App的receive方法
  // props: ["addTodo"],
};
</script>

<style scoped>
/*header*/
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

/* 1.border占用空间,outline不占用空间,不会影响元素的尺寸和位置。
2.border 可应用于几乎所有有形的html元素,而 outline 是针对链接、表单控件和ImageMap等元素设计 */
.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),
    0 0 8px rgba(82, 168, 236, 0.6);
}
</style>