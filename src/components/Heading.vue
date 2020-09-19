<template>
  <div class="field has-addons">
    <input
      type="range"
      min="0"
      max="360"
      value="50"
      v-model="heading"
      @change="set"
    />
    <p class="control">
      <button class="button" @click="increment">
        Heading +
      </button>
    </p>
    <p class="control">
      <input class="input" type="text" readonly v-model="heading" />
    </p>
    <p class="control">
      <button class="button" @click="decrement">
        Heading -
      </button>
    </p>
  </div>
</template>

<script>
import { ref } from "@vue/composition-api";

const API_URL =
  "http://192.168.100.168:3030/api/Write?event=KEY_HEADING_BUG_SET&data=";

function useHeading() {
  const heading = ref(0);

  function set() {
    fetch(API_URL + heading.value)
      .then(console.log("KEY_HEADING_BUG_SET send"))
      .catch((err) => console.log(err));
  }

  function increment() {
    heading.value++;
    fetch(API_URL + heading.value)
      .then(console.log("KEY_HEADING_BUG_SET send"))
      .catch((err) => console.log(err));
  }

  function decrement() {
    heading.value--;
    fetch(API_URL + heading.value)
      .then(console.log("KEY_HEADING_BUG_SET send"))
      .catch((err) => console.log(err));
  }

  return {
    set,
    heading,
    increment,
    decrement,
  };
}

export default {
  setup() {
    const reactiveContext = useHeading();

    return reactiveContext;
  },
};
</script>
