<template>
  <div class="my-account-wrapper">
    <RegisterComponent />
  </div>
</template>

<script>
// import Login from "@/components/Login.vue";
import RegisterComponent from "@/components/Register.vue";

export default {
  name: "Register",
  components: {
    // Login,
    RegisterComponent,
  },
};
</script>

<style scoped lang="scss"></style>
