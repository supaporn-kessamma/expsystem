<template>
    <v-app dark>
      <Header 
        :show="isShow"
        @color="toggleTheme"
        @toggle="toggleSidebar"
      />
        <Sidebar
          :show="isShow"
          :color="color"
        />
      <v-main>
        <v-container>
          <Nuxt />
        </v-container>
      </v-main>
      <Footer
          :color="color"
      />
    </v-app>
  </template>
  
  <script>
import Header from '../components/Header.vue';
  import Sidebar from '../components/Sidebar.vue';
  import Footer from '../components/Footer.vue';
  export default {
    name: 'LoginLayout',
    data() {
      return {
        components: {
            Header,
            Sidebar,
            Footer,
        },
        color: '#B71C1C',
        isShow: false,
      }
    },
    methods: {
        toggleTheme(color) {
            this.color = color
        },
        toggleSidebar(boolean){
            this.isShow = boolean
        },
    },
}
</script>

<style scoped>
</style>
  