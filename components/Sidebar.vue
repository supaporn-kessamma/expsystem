<template>
  <div>
    <v-navigation-drawer
      v-model="show"
      :mini-variant="miniVariant"
      fixed
      app
      :color="$vuetify.theme.dark ? color : $vuetify.theme.light ? color : ''"
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
    props: {
      show: {
        type: Boolean,
        default: false,
      },
      color: {
        type: String,
        default: '#B71C1C'
      }
    },
    data(){
      return {
        items: [
            {
              icon: '',
              title: 'Home',
              to: '/',
            },
            {
              icon: '',
              title: 'Register',
              to: '/register',
            },
            {
              icon: '',
              title: 'Login',
              to: '/login',
            },
          ],
        miniVariant: false,
        title: 'Vuetify.js',
        toggle: false,
      }
    },
}
</script>

<style scoped>
</style>