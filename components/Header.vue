<template>
  <v-app-bar 
    fixed 
    app 
    :color="$vuetify.theme.dark ? color : $vuetify.theme.light ? color : ''"
  >
    <v-app-bar-nav-icon @click="toggle" />
    <v-spacer></v-spacer>
      <div class="pa-4 mx-2 redBlack rounded-circle d-inline-block" @click="toggleTheme('red')"></div>
      <div class="pa-4 mx-2 blueWhite rounded-circle d-inline-block" @click="toggleTheme('blue')"></div>
      <div class="pa-4 mx-2 blackGold rounded-circle d-inline-block" @click="toggleTheme('gold')"></div>
  </v-app-bar>
</template>

<script>
export default {
  props: {
    show: {
      type: Boolean,
      default: false,
    },
  },
  data(){
    return {
      drawer: this.show,
      color: "#B71C1C",
    }
  },
  methods: {
    toggle(){
      this.$emit('toggle', !this.show)
    },
    toggleTheme(color) {
      if (color === "red") {
        this.color = "#B71C1C";
        this.$vuetify.theme.dark = true;
        this.$vuetify.theme.light = false;
        this.$emit('color', this.color)
      }
      else if (color === "blue") {
        this.color = "#1976D2";
        this.$vuetify.theme.dark = false;
        this.$vuetify.theme.light = true;
        this.$emit('color', this.color)
      }
      else if (color === "gold") {
        this.color = "#D4AF37";
        this.$vuetify.theme.dark = true;
        this.$vuetify.theme.light = false;
        this.$emit('color', this.color)
      }
    },
  },
}
</script>

<style scoped>
  .redBlack {
    background: linear-gradient( -90deg, #000000, #000000 50%, #B71C1C 50% );
    border: #ffffff 1px solid;
  }
  .blueWhite{
    background: linear-gradient( -90deg, #1976D2, #1976D2 50%, #ffffff 50% );
    border: #ffffff 1px solid;
  }
  .blackGold{
    background: linear-gradient( -90deg, #000000, #000000 50%, #D4AF37 50% );
    border: #ffffff 1px solid;
  }
</style>