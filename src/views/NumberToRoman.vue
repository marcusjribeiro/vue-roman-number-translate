<script setup lang="ts">
import { ref } from "vue";

const number = ref<number>();
const result = ref<string | number>();

const convert = () => {
  if (number.value && Number(number.value)) {
    console.log("number.value", number.value);
    return (
      (result.value = Number(number.value) + 1) && (number.value = undefined)
    );
  }
  console.log("oi");
  result.value = `Please type a number`;
  number.value = undefined;
};
</script>

<template>
  <div>
    <form @submit.prevent="convert">
      <input
        v-model="number"
        @keypress.enter.prevent="convert"
        class="text-emerald-500 font-bold border border-solid border-emerald-800 p-2 box-border"
      />
      <button type="submit">CONVERT</button>
    </form>
    <h1>{{ result }}</h1>
  </div>
</template>
