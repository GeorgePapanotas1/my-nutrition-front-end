<template>
  <div class="my-account-wrapper">
    <LoginComponent />
  </div>
</template>

<script>
// import Login from "@/components/Login.vue";
import LoginComponent from "@/components/Login.vue";

export default {
  name: "Register",
  components: {
    // Login,
    LoginComponent,
  },
};
</script>

<style scoped lang="scss"></style>
