<template>
  <div class="container">
    <div class="text-h4 my-4">Login</div>
    <v-form
    ref="form"
    v-model="valid"
    lazy-validation
    class="px-4"
  >
    <v-text-field
      v-model="username"
      :rules="usernameRules"
      label="Username"
      required
    ></v-text-field>

    <v-text-field
      v-model="password"
      :rules="passwordRules"
      label="Password"
      type="password"
      required
    ></v-text-field>

    <v-btn
      color="success"
      class="mr-4"
      @click="submit"
    >
      submit
    </v-btn>
  </v-form>
  </div>
</template>

<script>
export default {
  name: 'Login',
  layout: 'login',
  data(){
    return {
      valid: true,
      username: '',
      password: '',
      usernameRules: [
        v => !!v || 'Username is required',
        v => (v.slice(0,2) === '09' || v.slice(0,2) === '08' || v.slice(0,2) === '06') || 'example : 0998765432',
        v => (Number(v)) || 'example : 0998765432',
        v => (v && v.length === 10) || 'Username must not exceed 10 characters',
        v => (!!v.match(/^([0-9])+$/i)) || 'Do not enter special characters',
      ],
      passwordRules: [
        v => !!v || 'Password is required',
        v => (v.charAt(0) === v.charAt(0).toUpperCase()) || 'example : Aa123456',
        v => (!v.charAt(0).match(/^([0-9])+$/i)) || 'example : Aa123456',
        v => (!!v.match(/^([a-z0-9])+$/i)) || 'Do not enter special characters',
      ],
    }
  },
  methods: {
    submit () {
      if (this.$refs.form.validate()) {
        this.$router.push('/')
      }
    },
  },
}
</script>
