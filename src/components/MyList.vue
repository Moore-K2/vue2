<template>
  <ul class="todo-main">
    <!-- 使用子组件MyItem, v-for进行遍历，props进行传值, 绑定了:才表示传入的表达式或对象，
    而不是普通字符串值todo是key,"todoObj"是值 -->
    <MyItem
      v-for="todoObj in todolist"
      :key="todoObj.id"
      :todo="todoObj"
      :checkTodo="checkTodo"
      :deleteTodo="deleteTodo"
    ></MyItem>
  </ul>
</template>

<script scoped>
// 引入组件
import MyItem from "./MyItem.vue";
export default {
  name: "MyList",
  //注册组件
  components: { MyItem },
  data() {
    return {};
  },
  // 接收来自App父组件的数组todolist
  props: ["todolist", "checkTodo", "deleteTodo"],
};
</script>

<style scoped>
/*  */
/*main*/
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