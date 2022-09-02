<template>
  <div class="container">
    <div class="text-h4 my-4">Register</div>
    <v-form
      ref="form"
      v-model="valid"
      lazy-validation
      class="px-4"
    >
      <v-text-field
        v-model="form.name"
        :rules="rules.nameRules"
        label="Name"
        required
      ></v-text-field>
  
      <v-text-field
        v-model="form.lastname"
        :rules="rules.lastnameRules"
        label="Lastname"
        required
      ></v-text-field>

      <v-select
        v-model="form.bankname"
        :items="banks"
        :rules="rules.banknameRules"
        label="Bankname"
        data-vv-name="select"
        required
      ></v-select>

      <v-text-field
        v-model="form.account"
        :rules="rules.accountRules"
        label="Bank Account"
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

    <v-alert
      v-if="isAlert"
      dense
      type="error"
      class="mt-4"
    >
      name or lastname must be Thai or English only.
    </v-alert>

    <ShowDetail 
      :show="isShow"
      :form="form"
      @closeDialog="closeDialog"
    />
  </div>
</template>

<script>
import ShowDetail from '../components/ShowDetail.vue'
export default {
  name: 'Login',
  layout: 'guest',
  data(){
    return {
      components: {
        ShowDetail,
      },
      valid: true,
      form: {
        name: '',
        lastname: '',
        bankname: null,
        account: '',
      },
      banks: [
        'กรุงเทพ',
        'กสิกร',
        'ไทยพาณิช',
      ],
      rules: {
        nameRules: [
        v => !!v || 'Name is required',
        v => (!!v.match(/^([ก-๏])+$/i) || !!v.match(/^([a-z])+$/i)) || 'name must be Thai or English only.',
      ],
      lastnameRules: [
        v => !!v || 'Lastname is required',
        v => (!!v.match(/^([ก-๏])+$/i) || !!v.match(/^([a-z])+$/i)) || 'lastname must be Thai or English only.',
      ],
      banknameRules: [
        v => !!v || 'Bank is required',
      ],
      accountRules: [
        v => !!v || 'Bank Account is required',
        v => (Number(v)) || 'example : 0123456789',
        v => (v && v.length === 10) || 'Bank Account must not exceed 10 characters',
        v => (!!v.match(/^([0-9])+$/i)) || 'Do not enter special characters',
      ],
      },
      isAlert: false,
      isShow: false,
    }
  },
  methods: {
    submit () {
      if (!!this.form.name.match(/^([ก-๏])+$/i) === !!this.form.lastname.match(/^([ก-๏])+$/i) || !!this.form.name.match(/^([a-z])+$/i) === !!this.form.lastname.match(/^([a-z])+$/i)) {
        if (this.$refs.form.validate()) {
            this.isShow = true
        }
      }
      else {
        this.isAlert = true
        setTimeout(() => { 
          this.isAlert = false; 
        }, 3000)
      }
    },
    closeAlert(){
      this.isAlert = false
    },
    closeDialog(boolean){
      this.isShow = boolean
    },
  },
}
</script>
