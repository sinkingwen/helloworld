<template>
  <div class="hello">
    <div class="box1">
      <h1>HelloWorld</h1>
      <h2>{{ tag }}: {{ count }}</h2>
      <div id="demo" v-on:click="update">{{ message }}</div>
      <button v-on:click="addCount">count++</button>
    </div>

    <div class="box2">
      <button @click="awesome = !awesome">Toggle</button>
      <h1 v-if="awesome">Vue is awesome!</h1>
      <h1 v-else>Oh no 😢</h1>
      <div v-if="type === 'A'">A</div>
      <div v-else-if="type === 'B'">B</div>
      <div v-else-if="type === 'C'">C</div>
      <div v-else>Not A/B/C</div>
      <h1 v-show="ok">Hello!</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      message: "Vue3",
      count: 0,
      tag: "数量",
      awesome: true,
      type: 'A',
      ok:false
    };
  },
  methods: {
    update() {
      this.message += " !!!";
    },
    addCount() {
      this.count++;
    },
  },
  created() {
    console.log(this.tag, this.count);
  },
};
</script>

<style>
@media (min-width: 1024px) {
  .hello {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
  .box1 {
    width: 200px;
  }
  button {
    width: 80px;
    height: 40px;
    border-radius: 5px;
  }
}
</style>
