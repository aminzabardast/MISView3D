<template>
    <div id="speed-dial">
        <v-speed-dial bottom right v-model="fab">
            <template v-slot:activator>
                <v-btn v-model="fab" color="blue darken-2" dark fab>
                    <v-icon>account_circle</v-icon>
                    <v-icon>close</v-icon>
                </v-btn>
            </template>
            <v-btn fab dark small color="green">
                <v-icon>edit</v-icon>
            </v-btn>
            <v-btn fab dark small color="indigo">
                <v-icon>add</v-icon>
            </v-btn>
            <v-btn fab dark small color="red">
                <v-icon>delete</v-icon>
            </v-btn>
        </v-speed-dial>
    </div>
</template>

<script>
    export default {
        name: "SpeedDial",
        data () {
            return {
                fab: false
            }
        }
    }
</script>

<style scoped>
    div#speed-dial {
        position: fixed;
        bottom: 0;
        right: 0;
        z-index: 2;
    }
</style>