<template>
  <v-app :dark="darkTheme">

    <SpeedDial @invertTheme="darkTheme = !darkTheme"/>

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
    },
    data () {
      return {
        darkTheme: false
      }
    }
  }
</script>
