<template>
  <div class="field has-addons">
    <p class="control">
      <button class="button" @click="increment">
        Altimeter +
      </button>
    </p>
    <p class="control">
      <button class="button" @click="decrement">
        Altimeter -
      </button>
    </p>
  </div>
</template>

<script>
import { ref } from "@vue/composition-api";

const API_URL = "http://ip:port/api/Write?event=";

function useAltimeter() {
  const altimeter = ref(0);

  function increment() {
    altimeter.value++;
    fetch(API_URL + "KEY_KOHLSMAN_INC")
      .then(console.log("KEY_KOHLSMAN_INC send"))
      .catch((err) => console.log(err));
  }

  function decrement() {
    altimeter.value--;
    fetch(API_URL + "KEY_KOHLSMAN_DEC")
      .then(console.log("KEY_KOHLSMAN_DEC send"))
      .catch((err) => console.log(err));
  }

  return {
    altimeter,
    increment,
    decrement,
  };
}

export default {
  setup() {
    const reactiveContext = useAltimeter();

    return reactiveContext;
  },
};
</script>
