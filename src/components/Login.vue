<template>
  <div class="login-wrapper">
    <div class="login-inner-wrapper">
      <h2>Log in to Nutrio</h2>
      <p v-if="error" class="error_message">
        These credentials do not match our records
      </p>
      <div class="single-auth-item">
        <label for="_nutrio_username">Email</label>
        <b-form-input
          type="email"
          name="_nutrio_email"
          id="_nutrio_email"
          placeholder="Enter your email"
          v-model="email"
        ></b-form-input>
      </div>
      <div class="single-auth-item">
        <label for="_nutrio_password">Password</label>
        <b-form-input
          name="_nutrio_password"
          id="_nutrio_password"
          type="password"
          placeholder="Enter your password"
          v-model="password"
        ></b-form-input>
      </div>
      <div class="submit-button">
        <button class="green-button" type="submit" @click="login">
          Log in
        </button>
      </div>
      <div class="register-item">
        <p>
          Don't have an account yet? Create one
          <router-link class="router-link" to="/register">here</router-link>!
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      email: null,
      password: null,
      error: false,
    };
  },
  methods: {
    login: function () {
      const apiUrl = "http://127.0.0.1:8000";

      axios
        .post(`${apiUrl}/api/login`, {
          email: this.email,
          password: this.password,
        })
        .then((response) => {
          const token = response.data.success.token;
          this.$cookie.set("usg_tkn", token, 1);
          this.$router.push("/dashboard");
        })
        .catch(() => {
          this.error = true;
        });
    },
  },
};
</script>

<style scoped lang="scss">
.login-wrapper {
  .login-inner-wrapper {
    width: 50%;
    margin: auto;
    background-color: #f2eec9;
    padding: 50px 100px 70px;
    border-radius: 8px;
    box-shadow: 0 20px 20px 0 rgb(0 0 0 / 20%);

    .single-auth-item {
      display: flex;
      align-items: baseline;
      flex-direction: column;
      width: 90%;
      margin: 40px auto;
    }

    .error_message {
      color: #9e2e2e;
      line-height: 2;
      font-size: 14px;
    }

    h2 {
      color: #6d235c;
      margin-bottom: 25px;
    }

    label {
      color: #6d235c;
    }

    input {
      color: #6d235c;
    }

    .register-item {
      margin-top: 20px;

      .router-link {
        color: #6d235c !important;
      }

      .router-link:hover {
        text-decoration: none;
      }
    }
  }

  h2 {
    text-align: center;
  }

  .green-button {
    margin-top: 20px;
    padding: 12px 64px;
  }
}
</style>
