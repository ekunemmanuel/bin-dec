<template>
  <div
    class="grid min-h-screen p-[10px] place-items-center text-white bg-[#242424]"
  >
    <div class="max-w-[600px] w-full space-y-[30px]">
      <div class="">
        <h1 class="text-center capitalize text-[40px] flex-1">
          Binary to Decimal
        </h1>
      </div>
      <div class="p-[10px] rounded-lg space-y-4 bg-[#3c3c3c]">
        <div class="space-x-4 flex">
          <input
            class="w-full rounded-lg p-[5px] text-black"
            v-model="binValue"
            id="binary"
            type="text"
            placeholder="Enter binary number"
            :class="{
              'outline-red-500 ': isValid,
            }"
          />
        </div>
        <span class="text-red-400">
          {{ errorMessage }}
        </span>
        <div>
          <span
            class="w-full rounded-lg p-[5px] block bg-[#646464] text-center text-white"
            >{{ decValue }}</span
          >
        </div>
      </div>
      <div class="space-x-2 flex justify-center items-center">
        <span class="hover:text-[#7b7a7a] duration-200">
          <a href="https://github.com/ekunemmanuel/bin-dec" target="_blank">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="35"
              height="35"
              viewBox="0 0 24 24"
            >
              <path
                fill="currentColor"
                d="M12 2A10 10 0 0 0 2 12c0 4.42 2.87 8.17 6.84 9.5c.5.08.66-.23.66-.5v-1.69c-2.77.6-3.36-1.34-3.36-1.34c-.46-1.16-1.11-1.47-1.11-1.47c-.91-.62.07-.6.07-.6c1 .07 1.53 1.03 1.53 1.03c.87 1.52 2.34 1.07 2.91.83c.09-.65.35-1.09.63-1.34c-2.22-.25-4.55-1.11-4.55-4.92c0-1.11.38-2 1.03-2.71c-.1-.25-.45-1.29.1-2.64c0 0 .84-.27 2.75 1.02c.79-.22 1.65-.33 2.5-.33c.85 0 1.71.11 2.5.33c1.91-1.29 2.75-1.02 2.75-1.02c.55 1.35.2 2.39.1 2.64c.65.71 1.03 1.6 1.03 2.71c0 3.82-2.34 4.66-4.57 4.91c.36.31.69.92.69 1.85V21c0 .27.16.59.67.5C19.14 20.16 22 16.42 22 12A10 10 0 0 0 12 2"
              ></path></svg
          ></a>
        </span>
        <span class="hover:text-[#7b7a7a] duration-200">
          <a href="https://emmanuelapabiekun.vercel.app/" target="_blank">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="35"
              height="35"
              viewBox="0 0 24 24"
            >
              <path
                fill="currentColor"
                d="M12 12q-1.65 0-2.825-1.175T8 8q0-1.65 1.175-2.825T12 4q1.65 0 2.825 1.175T16 8q0 1.65-1.175 2.825T12 12m-8 8v-2.8q0-.85.438-1.562T5.6 14.55q1.55-.775 3.15-1.162T12 13q1.65 0 3.25.388t3.15 1.162q.725.375 1.163 1.088T20 17.2V20z"
              /></svg
          ></a>
        </span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, watch, computed } from "vue";

const binValue = ref();
const decValue = ref<number | string>(0);
const isValid = ref(false);
const errorMessage = ref<string | null>(null);
const disabled = ref(false);

const isDisabled = computed(() => disabled.value || isValid.value);

// validating the number is 1 or 0
watch(binValue, (val) => {
  if (val.match(/^[0-1]+$/)) {
    errorMessage.value = null;
    isValid.value = false;
    disabled.value = false;
    convertToDecimal();
  } else {
    isValid.value = true;
    errorMessage.value = "Please enter a valid binary number either 0 or 1";
    decValue.value = "error";
  }
  if (val === "") {
    errorMessage.value = null;
    isValid.value = false;
    disabled.value = true;
    decValue.value = 0;
  }
});

const convertToDecimal = () => {
  // let decimal = 0;
  // for (let i = binValue.value.length - 1, j = 0; i >= 0; i--, j++) {
  //   decimal += parseInt(binValue.value[i]) * Math.pow(2, j);
  // }
  decValue.value = parseInt(binValue.value, 2);
};
</script>
