<template>
  <v-app light>

    <SpeedDial/>

    <v-content>
      <router-view/>
    </v-content>

  </v-app>
</template>

<script>
  import SpeedDial from './components/SpeedDial'

  export default {
    name: 'App',
    components: {
      SpeedDial
    }
  }
</script>
