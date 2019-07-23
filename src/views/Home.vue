<template>
  <v-container fluid fill-height>
    <v-layout align-center justify-center>
      <v-flex xs12 sm8 md8 lg6>
        <v-card class="elevation-2">

          <v-toolbar class="elevation-0">
            <v-toolbar-title class="hidden-sm-and-down">Minimally Invasive Surgery View 3D Dataset</v-toolbar-title>
            <v-toolbar-title class="hidden-md-and-up">MISView3D Dataset</v-toolbar-title>
            <v-spacer></v-spacer>
            <v-tooltip bottom>
              <v-btn icon large target="_blank" slot="activator">
                <v-icon large>dashboard</v-icon>
              </v-btn>
              <span>Hint</span>
            </v-tooltip>
          </v-toolbar>

          <v-card-text>
            <p class="body-2 mt-1 mb-0">
              Jump to ...
            </p>
            <ul class="mt-0">
              <li>
                <a @click="goTo('summary')">Summary</a>
              </li>
              <li>
                <a @click="goTo('sample')">Sample Set</a>
              </li>
              <li>
                <a @click="goTo('partial-downloads')">Partial Downloads</a>
              </li>
              <li>
                <a @click="goTo('complete-download')">Complete Downloads</a>
              </li>
              <li>
                <a @click="goTo('format')">Data Format And Structure</a>
              </li>
              <li>
                <a @click="goTo('change-log')">Go To Change Logs</a>
              </li>
              <li>
                <a @click="goTo('contact')">Contact Information</a>
              </li>
            </ul>

            <h3 class="display-1 mt-5 mb-4" id="name-summary">
              Summary
            </h3>
            <p class="body-2">
              This dataset contains nearly 10.000 stereo images.
              These images are synthesized using <a href="https://blender.org/" target="_blank">Blender</a>&reg; open-source 3D computer graphics software.
              Each image have a <code>512x512</code> resolution.
            </p>

            <h3 class="display-1 mt-5 mb-4" id="name-sample">
              Sample Set
            </h3>
            <v-layout wrap class="hidden-sm-and-down">
              <v-flex xs12 sm6 md4>
                <v-img src="sample_images/1.png"></v-img>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-img src="sample_images/2.png"></v-img>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-img src="sample_images/3.png"></v-img>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-img src="sample_images/4.png"></v-img>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-img src="sample_images/5.png"></v-img>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-img src="sample_images/6.png"></v-img>
              </v-flex>
            </v-layout>
            <v-layout wrap class="hidden-md-and-up">
              <v-flex xs12 sm6 md4>
                <v-img src="sample_images/1.png"></v-img>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-img src="sample_images/4.png"></v-img>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-img src="sample_images/2.png"></v-img>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-img src="sample_images/5.png"></v-img>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-img src="sample_images/3.png"></v-img>
              </v-flex>
              <v-flex xs12 sm6 md4>
                <v-img src="sample_images/6.png"></v-img>
              </v-flex>
            </v-layout>
            <ul class="mt-4">
              <li>
                X Samples
              </li>
              <li>
                Included RGB images in PNG format, and disparity maps in PFM format.
              </li>
              <li>
                xxx Megabytes
              </li>
            </ul>

            <h3 class="display-1 mt-5 mb-4" id="name-partial-downloads">
              Partial Downloads
            </h3>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>

            <h3 class="display-1 mt-5 mb-4" id="name-complete-download">
              Complete Download
            </h3>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>

            <h3 class="display-1 mt-5 mb-4" id="name-format">
              Data Format And Structure
            </h3>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>

            <h3 class="display-1 mt-5 mb-4" id="name-change-log">
              Change Log
            </h3>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>

            <h3 class="display-1 mt-5 mb-4" id="name-contact">
              Contact Information
            </h3>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
            <p class="body-2">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda commodi cum, deleniti dicta dolor dolore earum eum eveniet excepturi, exercitationem explicabo facilis neque nihil perferendis quisquam quo ratione velit voluptates.
            </p>
          </v-card-text>

          <v-card-actions>
            <v-btn depressed>left</v-btn>
            <v-spacer></v-spacer>
            <v-btn depressed>right</v-btn>
          </v-card-actions>

        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  import * as $ from 'jquery'

  export default {
    components: {
    },
    methods: {
      goTo (section) {
        $("html, body").animate({
          scrollTop: $(`#name-${section}`).offset().top
        }, "fast");
      }
    }
  }
</script>

<style scoped>
</style>
