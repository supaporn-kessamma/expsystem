<template>
  <div class="text-center">
    <v-dialog
      v-model="show"
      persistent
      width="500"
    >
      <v-card>
        <v-card-title class="text-h5">
          details
        </v-card-title>

        <v-card-text>
          <p>Name: {{ form.name }}</p>
          <p>Lastname: {{ form.lastname }}</p>
          <p>Bank: {{ form.bankname }}</p>
          <p>Bank Account: {{ form.account }}</p>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="error"
            text
            @click="close"
          >
            close
          </v-btn>
          <v-btn
            color="primary"
            text
            @click="submit"
          >
            submit
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
    props: {
        show: {
          type: Boolean,
          default: false
        },
        form: {
            type: Object,
            default: () => {}
        },
    },
    data () {
      return {
        dialog: null,
      }
    },
    methods: {
      close(){
        this.$emit('closeDialog', false)
      },
      submit(){
        this.$router.push('/')
      },
    },
}
</script>

<style>

</style>