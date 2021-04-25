<template>
  <div>
    <DashboardComponent />
    <TestCalendar />
  </div>
</template>

<script>
import DashboardComponent from "../components/DashboardComponent";
import TestCalendar from "../components/TestCalendar";
export default {
  components: {
    DashboardComponent,
    TestCalendar,
  },
  beforeMount: function () {
    const token = this.$cookie.get("usg_tkn");
    if (!token) {
      this.$router.push("login");
    }
  },
};
</script>

<style></style>
