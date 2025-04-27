<template>
  <div>
    <form @submit.prevent class="relative">
      <input
        type="text"
        id="search"
        class="border-[0.5px] p-2 rounded-xl mt-20 w-[300px] outline-none"
        placeholder="Input a city"
        v-model="cityInput"
      />
      <button
        class="absolute top-0 right-0 bg-green-400 p-2 mt-20 rounded-xl flex items-center border border-green-400 cursor-pointer"
        @click="sendCity"
      >
        Search
      </button>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";

const emit = defineEmits(["emitCity"]);

const sendCity = () => {
  emit("emitCity", cityInput.value);
  console.log(cityInput.value);
};

const cityInput = ref("");
</script>
