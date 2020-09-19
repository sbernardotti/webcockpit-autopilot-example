<template>
  <div class="container">
    <h1 class="title">WebCockpit API example</h1>
    <Altimeter />
    <Heading />
  </div>
</template>

<script>
import Altimeter from "./components/Altimeter.vue";
import Heading from "./components/Heading.vue";

export default {
  name: "App",
  components: {
    Altimeter,
    Heading
  }
};
</script>

<style lang="css" scoped>
.container {
  margin-top: 60px;
}
</style>
