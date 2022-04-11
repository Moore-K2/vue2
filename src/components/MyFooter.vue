<template>
  <!-- v-show="x", 若x为0,boolean值为false，若x有值，boolean值为true -->
  <div class="todo-footer" v-show="total">
    <label>
      <input type="checkbox" :checked="isAll" @change="checkAll" />
    </label>
    <span>
      <span>已完成{{ doneTotal }}</span> / 全部{{ total }}
    </span>
    <button class="btn btn-danger" @click="clearAll">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: "MyFooter",
  data() {
    return {};
  },
  // props: ["todolist", "checkAllTodo", "clearAllDone"],
  props: ["todolist"],
  methods: {
    // 全选or全不选
    checkAll(event) {
      // console.log(event.target.checked);
      // this.checkAllTodo(event.target.checked);
      this.$emit("checkAllTodo", event.target.checked);
    },
    clearAll() {
      // if (confirm("真的要全部清除已勾选的所有任务吗？")) this.clearAllDone();
      if (confirm("真的要全部清除已勾选的所有任务吗？"))
        this.$emit("clearAllDone");
    },
  },

  // computed计算属性默认第一次加载的时候就开始监听
  computed: {
    // 统计数组长度
    total() {
      return this.todolist.length;
    },
    // 统计done的数量 方法1
    // doneTotal() {
    //   const arr = this.todolist.filter((todo) => {
    //     return todo.done;
    //   });
    //   return arr.length;
    // },
    // 统计done的数量 方法2
    // doneTotal2() {
    //   let i = 0;
    //   this.todolist.forEach((todo) => {
    //     if (todo.done) i++;
    //   });
    //   return i;
    // },
    // 统计done的数量 方法3，arr.reduce((preValue,curValue)=>{}, initialValue)
    // reduce() 方法对数组中的每个元素按序执行一个由您提供的 reducer 函数，
    // 每一次运行 reducer 会将先前元素的计算结果作为参数传入，最后将其结果汇总为单个返回值。
    doneTotal() {
      return this.todolist.reduce((pre, cur) => {
        return pre + (cur.done ? 1 : 0);
      }, 0);
      // return this.todolist.reduce((pre, cur) => pre + (cur.done ? 1 : 0), 0);
    },
    // 判断是否所有任务都已完成，完成了在footer勾选框里打钩,表示全选
    isAll() {
      return this.total === this.doneTotal && this.total > 0;
    },
  },
};
</script>

<style scoped>
/*  */
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
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