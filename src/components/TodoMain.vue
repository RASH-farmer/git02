<template>
  <div class="main">
    <ul>
      <li v-for="item in arr" :key="item.id">
        <div class="left">
          <input type="checkbox" v-model="item.ischeck" />
          <span>{{ item.id }}</span>
          <span :class="{ undeline: item.ischeck }">{{ item.name }}</span>
        </div>
        <button @click="delFn">删除</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    arr: {
      type: Array,
      required: true,
    },
  },
  methods: {
    delFn() {
      this.arr.splice(this.arr, 1);
      console.log(22);
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
button {
  margin-right: 30px;
}
span {
  margin: 0 60px;
}
li {
  margin: 8px 0 0 8px;
  /* border: 1px solid #000; */
  display: flex;
  justify-content: space-between;
  /* justify-content: space-around; */
  align-items: center;
  padding: 0 5px;
  height: 50px;
  line-height: 50px;
  font-size: 18px;
}
input[type="checkbox"] {
  margin-right: 20px;
  vertical-align: middle;
  width: 20px;
  height: 20px;
}
.undeline {
  text-decoration: line-through;
}
</style>