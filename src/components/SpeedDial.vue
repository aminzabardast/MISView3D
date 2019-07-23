<template>
    <div id="speed-dial">
        <v-speed-dial bottom right open-on-hover v-model="fab">
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
            <v-tooltip left v-if="showToTopBtn">
                <template v-slot:activator="{ on }">
                    <v-btn fab small v-on="on" @click="goToTop">
                        <v-icon>keyboard_arrow_up</v-icon>
                    </v-btn>
                </template>
                <span>Go To Top</span>
            </v-tooltip>
        </v-speed-dial>
    </div>
</template>

<script>
    import * as $ from 'jquery'

    export default {
        name: "SpeedDial",
        data () {
            return {
                fab: false,
                darkTheme: true,
                showToTopBtn: false,
                invertThemeTooltipText: 'Light Theme'
            }
        },
        methods: {
            invertTheme () {
                this.$emit('invertTheme');
                this.darkTheme = !this.darkTheme;
            },
            goToTop () {
                $("html, body").animate({ scrollTop: 0 }, "fast");
            },
            handleScroll () {
                this.showToTopBtn = $(window).scrollTop() > 100;
            }
        },
        watch: {
            darkTheme () {
                this.darkTheme ? this.invertThemeTooltipText = 'Light Theme' : this.invertThemeTooltipText = 'Dark Theme'
            }
        },
        created () {
            window.addEventListener('scroll', this.handleScroll);
        },
        destroyed () {
            window.removeEventListener('scroll', this.handleScroll);
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