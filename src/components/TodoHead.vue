<template>
  <div class="head">
    <h1>ToDo清单</h1>
    <input type="checkbox" v-model="isAll" />
    <input type="text" v-model="name" @keyup.enter="addFn" />
  </div>
</template>

<script>
export default {
  props: ["list"],
  data() {
    return {
      name: "",
    };
  },
  computed: {
    isAll: {
      set(checked) {
        this.list.forEach((item) => {
          item.ischeck = checked;
        });
      },
      get() {
        return (
          this.list.length !== 0 &&
          this.list.every((item) => {
            item.ischeck === true;
          })
        );
      },
    },
  },
  methods: {
    addFn() {
      if (this.name.trim().length === 0) {
        alert("内容不能为空");
        return;
      }
      this.$emit("create", this.name);
      this.name = "";
      console.log(1);
    },
  },
};
</script>

<style scoped>
.head {
  margin: 0 auto;
}
.head h1 {
  margin: 0 auto;
  text-align: center;
  margin-bottom: 20px;
}
input {
  display: inline-flex;
  margin: 0;
  padding: 0;
}
input[type="checkbox"] {
  vertical-align: middle;
  width: 10%;
  height: 20px;
  justify-content: space-around;
  border-radius: 5px;
}

.head input:last-child {
  width: 80%;
  height: 20px;
  line-height: 20px;
  font-size: 16px;
  padding: 8px;
}
</style>