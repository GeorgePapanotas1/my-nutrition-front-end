<template>
  <div class="home">
    <HelloWorld />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/Entrance.vue";

export default {
  name: "Home",
  components: {
    HelloWorld,
  },
};
</script>
