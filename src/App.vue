<template>
  <v-app>
    <v-content>
      <Header/>
      <router-view />
    </v-content>
  </v-app>
</template>

<script>
import Header from './components/layout/Header';

export default {
  name: 'App',
  components: {
    Header,
  },

  data: () => ({
    //
  }),
};
</script>
