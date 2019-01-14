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
        <input v-validate="'required|email'" id="email" v-model="email" class="input" name="email" type="email" />
        <span v-show="errors.has('email')" class="error">{{ errors.first('email') }}</span>
      </div>
      <div class="input-label">
        <label for="password" class="label">Password</label>
        <input id="password" type="password" v-model="password" class="input"  name="password" 
        v-validate="{ required: true, regex: /^[A-Z0-9]+[A-Z0-9]+[A-Z0-9]*$/i }" />
        <span v-show="errors.has('password')" class="error">{{ errors.first('password') }}</span>
      </div>
      <input type="submit" value="Sign Up" class="button" :disabled="errors.items.length > 0" />
    </form>
    <button class="button login-button">Login</button>
  </div>
</template>

<script>
import Vue from 'vue'
import woloxLogo from '../assets/wolox_logo.svg'
import VeeValidate from 'vee-validate'
Vue.use(VeeValidate)

export default {
  name: 'Registration',
  props: {},
  data () {
    return {
      firstName: null,
      lastName: null,
      email: null,
      password: null,
      woloxLogo: woloxLogo
    }
  },
  methods: {
    onSubmit () {
      let registrationData = {
        firstName: this.firstName,
        lastName: this.lastName,
        email: this.email,
        password: this.password
      }
      console.log(registrationData)
      this.firstName = null,
      this.lastName = null,
      this.email = null,
      this.password = null
    }
  }
}

const dict = {
  custom: {
    email: {
      required: 'Your email is empty'
    },
    name: {
      required: () => 'Your name is empty'
    }
  }
};
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

    &:disabled {
      background-color: $grey;
    }
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

    &:disabled {
      cursor: default;
    }
  }

  .login-button {
    background-color: transparent;
    border: 2px solid $green;
    color: $green;
  }

  .error {
    align-self: baseline;
    color: $red;
    font-size: 12px;
    margin: 5px;
  }
</style>
