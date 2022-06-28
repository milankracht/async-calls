<template>
  <v-app>
    <v-main>
      <MainLayout/>
    </v-main>
  </v-app>
</template>

<script>
import MainLayout from './components/MainLayout';

export default {
  name: 'App',

  components: {
    MainLayout,
  },

  data: () => ({
    //
  }),
};
</script>
