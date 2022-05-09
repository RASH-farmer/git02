<template>
  <div class="box">
    <todo-head :list="list" @create="createFn"></todo-head>
    <todo-main :arr="list"></todo-main>
    <!-- <todo-foot></todo-foot> -->
  </div>
</template>

<script>
import TodoFoot from "./components/TodoFoot.vue";
import TodoHead from "./components/TodoHead.vue";
import TodoMain from "./components/TodoMain.vue";
export default {
  components: { TodoHead, TodoMain, TodoFoot },
  data() {
    return {
      list: [
        { id: 100, name: "吃饭", ischeck: false },
        { id: 101, name: "睡觉", ischeck: false },
        { id: 102, name: "打豆豆", ischeck: false },
      ],
    };
  },
  methods: {
    createFn(name) {
      const id =
        this.list.length === 0 ? 100 : this.list[this.list.length - 1].id + 1;
      this.list.push({
        id: id,
        name: name,
        ischeck: false,
      });
    },
    // delFn(id) {
    //   let index = this.list.findIndex((item) => item.id === id);
    //   this.list.splice(index, 1);
    // },
  },
};
</script>

<style scoped>
.box {
  width: 520px;
  height: 500px;
  /* border: 1px solid #000; */
  margin: 0 auto;
}
</style>