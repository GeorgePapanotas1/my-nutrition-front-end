<template>
  <div class="login-wrapper">
    <div class="login-inner-wrapper">
      <h2>Register to Nutrio</h2>

      <div class="single-auth-item">
        <label for="_nutrio_email">Email</label>
        <b-form-input
          autocomplete="email"
          type="email"
          name="_nutrio_email"
          id="_nutrio_email"
          placeholder="Enter your email"
          v-model="email"
        ></b-form-input>
        <span v-if="errors.email" class="error_message">{{
          errors.email
        }}</span>
      </div>

      <div class="single-auth-item">
        <label for="_nutrio_first_name">First Name</label>
        <b-form-input
          autocomplete="first name"
          name="_nutrio_first_name"
          id="_nutrio_first_name"
          placeholder="Enter your first name"
          v-model="firstname"
        ></b-form-input>
        <span v-if="errors.firstname" class="error_message">{{
          errors.firstname
        }}</span>
      </div>

      <div class="single-auth-item">
        <label for="_nutrio_last_name">Last Name</label>
        <b-form-input
          autocomplete="last name"
          name="_nutrio_last_name"
          id="_nutrio_last_name"
          placeholder="Enter your last name"
          v-model="lastname"
        ></b-form-input>
        <span v-if="errors.last_name" class="error_message">{{
          errors.last_name
        }}</span>
      </div>

      <div class="single-auth-item">
        <label for="_nutrio_date_of_birth">Date of Birth</label>
        <b-form-input
          autocomplete="bday"
          name="_nutrio_date_of_birth"
          id="_nutrio_date_of_birth"
          placeholder="Enter your Date of Birth"
          type="date"
          v-model="date_of_birth"
        ></b-form-input>
        <span v-if="errors.date_of_birth" class="error_message">{{
          errors.date_of_birth
        }}</span>
      </div>
      <hr />
      <div class="single-auth-item">
        <label for="_nutrio_password">Password</label>
        <b-form-input
          name="_nutrio_password"
          id="_nutrio_password"
          type="password"
          placeholder="Enter your password"
          v-model="password"
        ></b-form-input>
        <span v-if="errors.password" class="error_message">{{
          errors.password
        }}</span>
      </div>

      <div class="single-auth-item">
        <label for="_nutrio_repeat_password">Repeat Password</label>
        <b-form-input
          name="_nutrio_repeat_password"
          id="_nutrio_repeat_password"
          type="password"
          v-model="c_password"
          placeholder="Enter your password"
        ></b-form-input>
        <span v-if="errors.c_password" class="error_message">{{
          errors.c_password
        }}</span>
      </div>

      <div class="submit-button">
        <button class="green-button" type="submit" @click="register">
          Register
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      firstname: null,
      lastname: null,
      email: null,
      password: null,
      c_password: null,
      date_of_birth: null,
      errors: {
        email: null,
        firstname: null,
        last_name: null,
        password: null,
        c_password: null,
        date_of_birth: null,
      },
    };
  },
  methods: {
    register: function () {
      const apiUrl = "http://127.0.0.1:8000";
      axios
        .post(`${apiUrl}/api/register`, {
          email: this.email,
          password: this.password,
          c_password: this.c_password,
          name: this.firstname,
          last_name: this.lastname,
          date_of_birth: this.date_of_birth,
        })
        .then(() => {
          this.$router.push("login");
        })
        .catch((err) => {
          let resp = err.response.data.error;

          if (resp.email) {
            this.errors.email = resp.email[0];
          }

          if (resp.name) {
            this.errors.firstname = resp.name[0];
          }

          if (resp.last_name) {
            this.errors.last_name = resp.last_name[0];
          }

          if (resp.date_of_birth) {
            this.errors.date_of_birth = resp.date_of_birth[0];
          }

          if (resp.password) {
            this.errors.password = resp.password[0];
          }

          if (resp.c_password) {
            this.errors.c_password = resp.c_password[0];
          }
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
      .error_message {
        color: #9e2e2e;
        line-height: 2;
        font-size: 14px;
      }
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
