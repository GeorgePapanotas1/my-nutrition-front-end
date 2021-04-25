<template>
  <h2 v-if="userData">Welcome {{ userData.name }} {{ userData.last_name }}</h2>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      apiUrl: "http://127.0.0.1:8000",
      userData: null,
    };
  },
  beforeMount: function () {
    const token = this.$cookie.get("usg_tkn");

    let config = {
      headers: {
        Accept: "application/json",
        Authorization: `Bearer ${token}`,
      },
    };

    axios
      .post(`${this.apiUrl}/api/details`, {}, config)
      .then((response) => {
        this.userData = response.data.success;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style></style>
