<template>
  <v-footer 
    absolute 
    app
    :color="$vuetify.theme.dark ? color : $vuetify.theme.light ? color : ''"
  >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
</template>

<script>
export default {
    props: {
      color: {
        type: String,
        default: '#B71C1C'
      }
    },

}
</script>

<style>

</style>