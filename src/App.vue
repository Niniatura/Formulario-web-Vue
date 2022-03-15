<template>
  <v-app>
    
    <v-main>
      <formulario-web/>
    </v-main>
  </v-app>
</template>

<script>
import FormularioWeb from './components/FormularioWeb.vue';

export default {
  name: 'App',

  components: {
    FormularioWeb,
  },

  data: () => ({
    //
  }),
};
</script>
