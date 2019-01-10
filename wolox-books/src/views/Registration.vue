<template>
  <div class="container">
    <div class="title">
      <img :src="woloxLogo" alt="wolox logo" class="wolox-logo" />
      <h4>BOOKS</h4>
    </div>
    <form @submit.prevent="onSubmit" class="form">
      <div class="input-label">
        <label for="firstName" class="label">First Name</label>
        <input id="firstName" v-model="firstName" class="input" />
      </div>
      <div class="input-label">
        <label for="lastName" class="label">Last Name</label>
        <input id="lastName" v-model="lastName" class="input" />
      </div>
      <div class="input-label">
        <label for="email" class="label">Email</label>
        <input id="email" v-model="email" class="input" />
      </div>
      <div class="input-label">
        <label for="password" class="label">Password</label>
        <input id="password" type="password" v-model="password" class="input" />
      </div>
      <input type="submit" value="Sign Up" class="button"/>
    </form>
    <button class="button login-button">Login</button>
  </div>
</template>

<script>
import woloxLogo from '../assets/wolox_logo.svg';

export default {
  name: 'Registration',
  props: {},
  data() {
    return {
      firstName: null,
      lastName: null,
      email: null,
      password: null,
      woloxLogo: woloxLogo
    }
  },
  methods: {
    onSubmit() {
      let registrationData = {
        firstName: this.firstName,
        lastName: this.lastName,
        email: this.email,
        password: this.password
      }
      console.log(registrationData);
      this.firstName = null,
      this.lastName = null,
      this.email = null,
      this.password = null
    }
  }
}
</script>

<style scoped lang="scss">
  @import "../scss/colors.scss";

  .container {
    background-color: $light-grey;
    border-top: 5px solid $blue;
    display: flex;
    flex-direction: column;
    padding: 15px;
    width: 300px;
  }

  .wolox-logo {
    width: 275px;
  }

  .form {
    border-bottom: 2px solid $darker-grey;
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
    padding-bottom: 20px;
  }

  .input-label {
    display: flex;
    flex-direction: column;
    margin-bottom: 15px;
  }

  .label {
    align-self: baseline;
    font-size: 14px;
    font-weight: bold;
    margin: 0 0 5px 10px;
  }

  .input,
  .button {
    border: none;
    border-radius: 5px;
  }

  .input {
    height: 30px;
    padding: 0 10px;
  }

  .button {
    background-color: $green;
    color: $white;
    font-size: 15px;
    font-weight: bold;
    height: 40px;

    &:hover {
      cursor: pointer;
    }
  }

  .login-button {
    background-color: transparent;
    border: 2px solid $green;
    color: $green;
  }
</style>
