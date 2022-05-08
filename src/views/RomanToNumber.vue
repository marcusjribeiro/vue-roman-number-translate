<script setup lang="ts">
import { ref } from "vue";

const romanNumber = ref<string>();
const result = ref<number>(0);

const romanDictionary = (romanN: string) => {
  const upperCaseRomanNum = romanN.toUpperCase();
  return (
    {
      I: 1,
      V: 5,
      X: 10,
      L: 50,
      C: 100,
      D: 500,
      M: 1000,
    }[upperCaseRomanNum] || -1
  );
};

const convert = (romanNum?: string) => {
  let i = 0;
  result.value = 0;
  if (romanNum && !romanNum?.toLocaleLowerCase().includes("iiii")) {
    if (romanDictionary(romanNum) > 0) {
      return (result.value = romanDictionary(romanNum));
    }

    for (let j = 0; j < romanNum.length; j++) {
      const element = romanDictionary(romanNum[j]);
      if (element <= 0) {
        romanNumber.value = undefined;
        return element;
      }
    }

    while (i < romanNum.length) {
      const num = romanDictionary(romanNum[i]);
      if (i + 1 === romanNum.length - 1) {
        const nextNum = romanDictionary(romanNum[i + 1]);
        if (nextNum > num) {
          result.value += nextNum - num;
          i++;
        } else {
          result.value += num + nextNum;
          i++;
        }
      } else {
        result.value += num;
      }
      i++;
    }
  }
  romanNumber.value = undefined;
};
</script>

<template>
  <div>
    <form @submit.prevent="convert(romanNumber)">
      <input
        v-model="romanNumber"
        @keypress.enter.prevent="convert(romanNumber)"
        class="text-emerald-500 font-bold border border-solid border-emerald-800 p-2 box-border rounded-xl"
      />
      <button
        class="ml-6 bg-emerald-400 p-2 rounded-full text-white font-bold"
        type="submit"
      >
        CONVERT
      </button>
    </form>
    <h1 class="mt-8">Result:</h1>
    <h2 v-if="result > 0" class="text-emerald-400 font-medium pl-4">
      {{ `Your result: ${result}` }}
    </h2>
    <h2 v-else class="text-red-400 font-medium pl-4">
      Please type an existing roman number
    </h2>
  </div>
</template>
