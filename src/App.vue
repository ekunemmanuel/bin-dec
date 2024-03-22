<template>
  <div
    class="grid min-h-screen p-[10px] place-items-center text-white bg-[#242424]"
  >
    <div class="max-w-[600px] w-full space-y-[30px]">
      <h1 class="text-center capitalize text-[40px]">Binary to Decimal</h1>
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
          <button
            class="bg-[#232222] rounded-lg px-[20px] py-[5px] hover:bg-[#646464] duration-200 text-white disabled:opacity-50 disabled:cursor-not-allowed hover:disabled:opacity-50"
            @click="convertToDecimal"
            :disabled="isDisabled"
          >
            Convert
          </button>
        </div>
        <span class="text-red-400">
          {{ errorMessage }}
        </span>
        <div>
          <span
            class="w-full rounded-lg p-[5px] block bg-[#646464] text-white"
            >{{ decValue }}</span
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, watch, computed } from "vue";

const binValue = ref();
const decValue = ref<number | null>(0);
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
