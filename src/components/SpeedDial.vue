<template>
    <div id="speed-dial">
        <v-speed-dial bottom right v-model="fab">
            <template v-slot:activator>
                <v-btn v-model="fab" fab>
                    <v-icon>more_vert</v-icon>
                    <v-icon>close</v-icon>
                </v-btn>
            </template>
            <v-tooltip left>
                <template v-slot:activator="{ on }">
                    <v-btn fab small v-on="on" @click="invertTheme">
                        <v-icon>invert_colors</v-icon>
                    </v-btn>
                </template>
                <span>{{invertThemeTooltipText}}</span>
            </v-tooltip>
        </v-speed-dial>
    </div>
</template>

<script>
    export default {
        name: "SpeedDial",
        data () {
            return {
                fab: false,
                darkTheme: true,
                invertThemeTooltipText: 'Light Theme'
            }
        },
        methods: {
            invertTheme () {
                this.$emit('invertTheme');
                this.darkTheme = !this.darkTheme;
            }
        },
        watch: {
            darkTheme () {
                this.darkTheme ? this.invertThemeTooltipText = 'Light Theme' : this.invertThemeTooltipText = 'Dark Theme'
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