<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-space></v-space>
        <h1>bluechip</h1>
      </div>

      <v-spacer></v-spacer>
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
    </v-app-bar>

    <v-main>
      <HelloWorld/>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>
