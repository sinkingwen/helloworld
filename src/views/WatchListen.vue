<template>
  <div>
    <p>
      Ask a yes/no question:
      <input v-model="question" :disabled="loading" />
    </p>
    <p>{{ answer }}</p>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

const question = ref("");
const answer = ref("Questions usually contain a question mark. ;-)");
const loading = ref(false);

// 可以直接侦听一个 ref
watch(question, async (newQuestion, oldQuestion) => {
  if (newQuestion.includes("?")) {
    loading.value = true;
    answer.value = "Thinking...";
    try {
      const res = await fetch("https://yesno.wtf/api");
      answer.value = (await res.json()).answer;
    } catch (error) {
      answer.value = "Error! Could not reach the API. " + error;
    } finally {
      loading.value = false;
    }
  }
});
</script>
<style scoped>
input {
  width: 200px;
  height: 50px;
  border: 1px solid green;
}
</style>