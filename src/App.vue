<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <!-- 使用组件 -->
        <!-- <TopHeader :addTodo="addTodo"></TopHeader> -->
        <!-- 用自定义事件实现 -->
        <TopHeader @addTodoEvent="addTodo"></TopHeader>
        <!-- 将todolist数组，checkTodo()方法，deleteTodo()方法，传入MyList组件 -->
        <MyList
          :todolist="todolist"
          :checkTodo="checkTodo"
          :deleteTodo="deleteTodo"
        ></MyList>
        <MyFooter
          :todolist="todolist"
          @checkAllTodo="checkAllTodo"
          @clearAllDone="clearAllDone"
        ></MyFooter>
      </div>
    </div>
  </div>
</template>

<script>
// 1 引入所有组件， 引入之前确保组件要暴露export default
import MyFooter from "./components/MyFooter.vue";
import TopHeader from "./components/TopHeader.vue";
import MyList from "./components/MyList.vue";

export default {
  name: "App",
  //  2 注册组件
  components: {
    TopHeader,
    MyFooter,
    MyList,
  },
  data() {
    return {
      // 定义一个数组对象用于存放数据.id不能用Number，因为js的Number是有限的，done是boolean
      todolist: JSON.parse(localStorage.getItem("todolist")) || [],
    };
  },
  methods: {
    // 绝！将addTodo方法传给header使用a
    addTodo(todoObj) {
      console.log("receive", todoObj);
      this.todolist.unshift(todoObj);
    },
    // 定义方法，勾选或取消勾选一个todo,操作todoObj的done,传给孙子，先给儿子，儿子再给儿子
    checkTodo(id) {
      this.todolist.forEach((todo) => {
        if (todo.id === id) todo.done = !todo.done;
      });
    },
    // 删除todo, filter()是不会改变原数组，返回的是新数组
    deleteTodo(id) {
      this.todolist = this.todolist.filter((todo) => {
        return todo.id !== id;
      });
    },
    // 传给footer组件。全选所有任务 完成or取消全选
    checkAllTodo(done) {
      this.todolist.forEach((todo) => {
        todo.done = done;
      });
    },
    // 删除所有done为完成的任务，交给footer按钮
    clearAllDone() {
      this.todolist = this.todolist.filter((todo) => {
        return !todo.done;
      });
    },
  },
  watch: {
    // 开启浏览器缓存，进行监视,可以监视method的unshift等方法。监视(newvalue,oldvalue)有两种类型：简写||深度
    // todolist(value) {
    //   // JSON.stringify将js对象转为字符串
    //   localStorage.setItem("todolist", JSON.stringify(value));
    // },
    // 要想监视todo对象里面的属性变化，需要开启深度监视
    todolist: {
      deep: true,
      handler(value) {
        localStorage.setItem("todolist", JSON.stringify(value));
      },
    },
  },
};
</script>

<style>
/*base*/
body {
  background: #fff;
}

.btn {
  display: inline-block;
  /* 行内块元素，让元素可以设置成一行（不独占一行），且可以设置宽高 */
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  /* 设置手形光标 */
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2),
    0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}

.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}

.btn:focus {
  outline: none;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.3);
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>