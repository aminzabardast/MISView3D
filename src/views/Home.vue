<template>
  <v-container fluid fill-height>
    <v-layout align-center justify-center>
      <v-flex xs12 sm8 md8 lg6>
        <v-card class="elevation-2">

          <v-toolbar class="elevation-0">
            <v-toolbar-title class="hidden-sm-and-down">Minimally Invasive Surgery View 3D Dataset</v-toolbar-title>
            <v-toolbar-title class="hidden-md-and-up">MISView3D Dataset</v-toolbar-title>
            <v-spacer></v-spacer>
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
                <a @click="goTo('format')">Data Format And Structure</a>
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

            <h3 class="display-1 mt-5 mb-4" id="name-format">
              Data Format And Structure
            </h3>
            Python users can use <a href="https://gist.github.com/aminzabardast/4e4e7414c462676b522c35834851da60" target="_blank">This IO library</a> to read and write PNG, and PFM files.

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
                {{sampleDownload.numbers}} Samples
              </li>
              <li>
                Included RGB images in PNG format, and disparity maps in PFM format.
              </li>
              <li>
                {{sampleDownload.size}}
              </li>
            </ul>
            <v-btn block @click="openInNewTab(sampleDownload.url)">
              <v-icon left>cloud_download</v-icon>
              Download Sample File ( <span class="file_name">.tar.gz </span> )
            </v-btn>

            <h3 class="display-1 mt-5 mb-4" id="name-partial-downloads">
              Partial Downloads
            </h3>
            <p class="body-2">
              Here is a partition of the whole dataset, for anyone who may need only parts of the dataset.
            </p>
            <v-data-table :headers="headers" :items="items" hide-actions class="elevation-0">
              <template slot="items" slot-scope="props">
                <td>{{ props.item.light }}</td>
                <td>
                  <div v-for="item in props.item.w" :key="item.name" class="pa-1">
                    {{item.name}} (
                    <a :href="item.train" target="_blank">Training</a> {{item.train_size}} |
                    <a :href="item.valid" target="_blank">Validation</a> {{item.valid_size}}
                    ) <br/>
                  </div>
                </td>
                <td>
                  <div v-for="item in props.item.wo" :key="item.name" class="pa-1">
                    {{item.name}} (
                    <a :href="item.train" target="_blank">Training</a> {{item.train_size}} |
                    <a :href="item.valid" target="_blank">Validation</a> {{item.valid_size}}
                    ) <br/>
                  </div>
                </td>
              </template>
            </v-data-table>

            <h3 class="display-1 mt-5 mb-4" id="name-complete-download">
              Complete Download
            </h3>
            <ul>
              <li>
                {{completeDownload.numbers}} Samples
              </li>
              <li>
                Included RGB images in PNG format, and disparity maps in PFM format.
              </li>
              <li>
                {{completeDownload.size}}
              </li>
            </ul>
            <v-btn block @click="openInNewTab(completeDownload.url)">
              <v-icon left>cloud_download</v-icon>
              Download Complete dataset ( <span class="file_name">.tar.gz </span> )
            </v-btn>

            <h3 class="display-1 mt-5 mb-4" id="name-contact">
              Contact Information
            </h3>
            <p class="body-2">
              For any information regarding the dataset, please contact <a href="emailto:zabardast.amin@metu.edu.tr">zabardast.amin@metu.edu.tr</a>.
            </p>
          </v-card-text>

        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  import * as $ from 'jquery'

  export default {
    data () {
      return {
        headers: [
          {
            text: '',
            align: 'left',
            sortable: false,
            value: 'light'
          },
          {
            text: 'Without Smoke',
            align: 'left',
            value: 'wo',
            sortable: false,
          },
          {
            text: 'With Smoke',
            align: 'left',
            value: 'w',
            sortable: false,
          },
        ],
        items: [
          {
            light: 'Low Light',
            w: [
              {
                  name: 'A1',
                  train:'https://drive.google.com/open?id=1Msn_ZnMLWLAbkpPPrwoxSUfeXdmbb6DW',
                  train_size: '293 MB',
                  valid: 'https://drive.google.com/open?id=1fsngdjC4IQ1UYkTbX-0IpFOMTidBrVBV',
                  valid_size: '33 MB',
              },
              {
                  name: 'A2',
                  train:'https://drive.google.com/open?id=1U6CzYTSqqZVViaxllMxHH5kk_DwGzc0V',
                  train_size: '287 MB',
                  valid: 'https://drive.google.com/open?id=13I6tQAtv6B6TBzrUxs4ExAjAmx4DGAMs',
                  valid_size: '33 MB',
              },
              {
                  name: 'A3',
                  train:'https://drive.google.com/open?id=1pTJwqFDMlvql3BKEGkYUvpMAevaRFUr8',
                  train_size: '298 MB',
                  valid: 'https://drive.google.com/open?id=1EMmpUT4BAsl6Q35H4422WLE12k7YSggy',
                  valid_size: '34 MB',
              },
              {
                  name: 'A4',
                  train:'https://drive.google.com/open?id=1JBIP88oMGz0RbacnG8-VM5KRCRmle0Sd',
                  train_size: '293 MB',
                  valid: 'https://drive.google.com/open?id=1wM3JId_iVeGZyodFjn0_akusdN2GEhKg',
                  valid_size: '33 MB',
              },
              {
                  name: 'A5',
                  train:'https://drive.google.com/open?id=1I8pCzV2LoUtOznlav4gbNHFgdeCqV_wc',
                  train_size: '291 MB',
                  valid: 'https://drive.google.com/open?id=1JjiP-Z5lAToAkmti7T719xe_IfEyvcKd',
                  valid_size: '33 MB',
              },
              {
                  name: 'A6',
                  train:'https://drive.google.com/open?id=1OPVkgLIPKUuWmYoi5-SVhcZwLx8srOok',
                  train_size: '288 MB',
                  valid: 'https://drive.google.com/open?id=1kGn17Sts5S6guez4z8ylNqFtd3f7webi',
                  valid_size: '33 MB',
              },
            ],
            wo: [
              {
                  name: 'D1',
                  train:'https://drive.google.com/open?id=1ObB3v8fxQ7ytMyK0pDRzN987i-RcuX5F',
                  train_size: '287 MB',
                  valid: 'https://drive.google.com/open?id=1Ej2HVAZeBcSTQidqaSuh-3Ab2-YSWho6',
                  valid_size: '31 MB',
              },
              {
                  name: 'D2',
                  train:'https://drive.google.com/open?id=12kg2OFJXCQDz_08pWOZVMZLw-URy22LC',
                  train_size: '283 MB',
                  valid: 'https://drive.google.com/open?id=1c04WgWSl1F3QxdxRmYFzIASCBLWmNlHh',
                  valid_size: '31 MB',
              },
              {
                  name: 'D3',
                  train:'https://drive.google.com/open?id=1rUwzASqAUYmzKLktrVfLlfDWg40GVrSw',
                  train_size: '292 MB',
                  valid: 'https://drive.google.com/open?id=1eW4xQPSPOCSNF0OFTVW7a-WcTKc6Eogm',
                  valid_size: '31 MB',
              },
              {
                  name: 'D4',
                  train:'https://drive.google.com/open?id=1pSxhG0zX0-HrVBpgklNnceyirBIgLwHH',
                  train_size: '288 MB',
                  valid: 'https://drive.google.com/open?id=1rYDd-oRPIamw1YWg5W5EkYE8d8w4lv4-',
                  valid_size: '32 MB',
              },
              {
                  name: 'D5',
                  train:'https://drive.google.com/open?id=1h2e5hbBZesojaK6TMmkLhLroEUb8JcLP',
                  train_size: '286 MB',
                  valid: 'https://drive.google.com/open?id=1hI6Q2FImooAW20p54wBYVPe-f1pDvjuY',
                  valid_size: '31 MB',
              },
              {
                  name: 'D6',
                  train:'https://drive.google.com/open?id=14JVvTScERvyFgNrJcjR-TLLfW9NsvobN',
                  train_size: '285 MB',
                  valid: 'https://drive.google.com/open?id=1isg014cjc06pUlRWIPpZvqb87Y6Wp1fJ',
                  valid_size: '32 MB',
              },
            ]
          },
          {
            light: 'Medium Light',
            w: [
              {
                  name: 'B1',
                  train:'https://drive.google.com/open?id=1tWOh7brY3kphPC9pi-bpPma6bb-mv8Wn',
                  train_size: '337 MB',
                  valid: 'https://drive.google.com/open?id=1vwyH8S-PIxHLUsfYUg6rYFWp7F3IXZyI',
                  valid_size: '38 MB',
              },
              {
                  name: 'B2',
                  train:'https://drive.google.com/open?id=1p9Zu8VfQoT3RByPbSKx2krUFL9UoFTGS',
                  train_size: '329 MB',
                  valid: 'https://drive.google.com/open?id=1qWZmBFpHdeMQLNzMtg1YxCWyyEDWuWCg',
                  valid_size: '37 MB',
              },
              {
                  name: 'B3',
                  train:'https://drive.google.com/open?id=1NrjQq2DyMJl9cCWxopw9AqaIncKWYzDY',
                  train_size: '339 MB',
                  valid: 'https://drive.google.com/open?id=1mfNzn7zntVNtQuyYd6f07RItf8rRO2rP',
                  valid_size: '38 MB',
              },
              {
                  name: 'B4',
                  train:'https://drive.google.com/open?id=1sXrEV8Pj1P5B8zzxgH7c1SUW_lDDZ1Ul',
                  train_size: '337 MB',
                  valid: 'https://drive.google.com/open?id=18WTq-R4VlUPPDAm9StIvVQTbu-HSu4KD',
                  valid_size: '39 MB',
              },
              {
                  name: 'B5',
                  train:'https://drive.google.com/open?id=18kj0gfXB7HtjM15JfRtngZq6y8Y7UVgR',
                  train_size: '332 MB',
                  valid: 'https://drive.google.com/open?id=1zIngAuK2eZanU5TL8Iomdldoyw56vtKP',
                  valid_size: '38 MB',
              },
              {
                  name: 'B6',
                  train:'https://drive.google.com/open?id=13pfvNmufZmUYcEZrexZxeNu-xNKdQxUy',
                  train_size: '334 MB',
                  valid: 'https://drive.google.com/open?id=1AnEDaBqOfgRxmy1O4FyZTnzXIKFC8mhz',
                  valid_size: '38 MB',
              },
            ],
            wo: [
              {
                  name: 'E1',
                  train:'https://drive.google.com/open?id=1CA_fRvEax9jeKpiq8xLf8KY-Im-KYaD_',
                  train_size: '323 MB',
                  valid: 'https://drive.google.com/open?id=1ol5pk34l95vRZeTDJfgFjdS_VhgTuNrV',
                  valid_size: '35 MB',
              },
              {
                  name: 'E2',
                  train:'https://drive.google.com/open?id=1FQv6rAP3RP62j894jVqwrcG9JpwkgaRY',
                  train_size: '318 MB',
                  valid: 'https://drive.google.com/open?id=1bBrv3nX6gcc6EhGz_AK3YQgsv7Hru5Gw',
                  valid_size: '35 MB',
              },
              {
                  name: 'E3',
                  train:'https://drive.google.com/open?id=1Jg12msZQET_etrQgpAqTvz9dRGP40Iky',
                  train_size: '327 MB',
                  valid: 'https://drive.google.com/open?id=1buwPTjyr_xgroJRmV7jrMYueCYFSstZ7',
                  valid_size: '35 MB',
              },
              {
                  name: 'E4',
                  train:'https://drive.google.com/open?id=1T_8YSXVZhWEK0JsXKJog2cqE8kug6yLc',
                  train_size: '325 MB',
                  valid: 'https://drive.google.com/open?id=1eFUdlqbm-Sj2Q4jWvo9SSgtLTNHHCtVR',
                  valid_size: '35 MB',
              },
              {
                  name: 'E5',
                  train:'https://drive.google.com/open?id=1mYOwiQJpC5GfytWQI7cgQTPlOeLTK_Xl',
                  train_size: '319 MB',
                  valid: 'https://drive.google.com/open?id=1R9rIEXBQTEpwMdkG5eHbdgTD9w0_BgN-',
                  valid_size: '35 MB',
              },
              {
                  name: 'E6',
                  train:'https://drive.google.com/open?id=1Od6mKXPsZXKStTno4_QM-e40NdBnCySZ',
                  train_size: '321 MB',
                  valid: 'https://drive.google.com/open?id=15XT31noiUBMjqueaV4Ac7dXAv2BfqMv8',
                  valid_size: '36 MB',
              },
            ]
          },
          {
            light: 'High Light',
            w: [
              {
                  name: 'C1',
                  train:'https://drive.google.com/open?id=11gcY6KpYtL1pMRNiReFHFWNHCAxBYhlM',
                  train_size: '356 MB',
                  valid: 'https://drive.google.com/open?id=1AL7inF4gSjp6jVLqJUA7lsj9GOwhpyV5',
                  valid_size: '41 MB',
              },
              {
                  name: 'C2',
                  train:'https://drive.google.com/open?id=1NPVLQsq9uDAYuF-mIphPhbESpE2CmkfE',
                  train_size: '343 MB',
                  valid: 'https://drive.google.com/open?id=12bPe5MjbnZc-LvomzzHSrLk6qGWBiFgL',
                  valid_size: '39 MB',
              },
              {
                  name: 'C3',
                  train:'https://drive.google.com/open?id=1bWvDfbNFCTyRrNl5zTQl0oF9XDXZ2JHb',
                  train_size: '360 MB',
                  valid: 'https://drive.google.com/open?id=1qVvp-3pD2wQsRYqk3gqOJZi630o2IFQU',
                  valid_size: '41 MB',
              },
              {
                  name: 'C4',
                  train:'https://drive.google.com/open?id=1SAYXmEM086uJVF1Vdp60nzVtXNkgt4nc',
                  train_size: '357 MB',
                  valid: 'https://drive.google.com/open?id=1kUq8j0PPU7bvVrwOylK1hfgGScnzx3nf',
                  valid_size: '41 MB',
              },
              {
                  name: 'C5',
                  train:'https://drive.google.com/open?id=1G6khjRN9aB_nDrVPG5y04kOHzIkaJak5',
                  train_size: '352 MB',
                  valid: 'https://drive.google.com/open?id=1V6SU6Dqeg6A4joKZkMsB5fhjNwIgklh4',
                  valid_size: '40 MB',
              },
              {
                  name: 'C6',
                  train:'https://drive.google.com/open?id=1VuHzQLdJICWFNne9ZPyzaMIjWoR5B8px',
                  train_size: '355 MB',
                  valid: 'https://drive.google.com/open?id=1OBwKV_GyKUt2XH6DZWwo6kxgfarSSIKg',
                  valid_size: '41 MB',
              },
            ],
            wo: [
              {
                  name: 'F1',
                  train:'https://drive.google.com/open?id=1yMpJ3UJR3qM8pUhhaHMDlXLXxxFEIArb',
                  train_size: '340 MB',
                  valid: 'https://drive.google.com/open?id=1bB3UaVgK1yC05u9sCCTZCdvFJl9liyWV',
                  valid_size: '37 MB',
              },
              {
                  name: 'F2',
                  train:'https://drive.google.com/open?id=1aIzbH3okJn3YEzscmZcrX6AM7NKuTUc8',
                  train_size: '336 MB',
                  valid: 'https://drive.google.com/open?id=1qrNtBYgwDxmGA_O0Ey3PzYmP-0hWlB1K',
                  valid_size: '37 MB',
              },
              {
                  name: 'F3',
                  train:'https://drive.google.com/open?id=1BBI_TXoaOclS32v0kZTOxIxm9U1bKk-n',
                  train_size: '348 MB',
                  valid: 'https://drive.google.com/open?id=1EJxA8QssPdt6cnTJzVJocu7FRl8KQCke',
                  valid_size: '38 MB',
              },
              {
                  name: 'F4',
                  train:'https://drive.google.com/open?id=1yGOrj8gS6hxTMRp2fyyvPL8IbENxLyS_',
                  train_size: '344 MB',
                  valid: 'https://drive.google.com/open?id=1CdKXjL1kh1Yc_3HkaYDUZ3xJ1ejgq5N9',
                  valid_size: '38 MB',
              },
              {
                  name: 'F5',
                  train:'https://drive.google.com/open?id=1e57RpAb4CVCiPDs8o03dTJmG6dzTSDqv',
                  train_size: '340 MB',
                  valid: 'https://drive.google.com/open?id=1AW9ZoRMpDP7Q8tg25l6W6HIt9aDGC2OW',
                  valid_size: '37 MB',
              },
              {
                  name: 'F6',
                  train:'https://drive.google.com/open?id=14pww11ifeZ9L_h5aOQ25a91eTgjl1GOZ',
                  train_size: '342 MB',
                  valid: 'https://drive.google.com/open?id=1uhRAg1kWlkRX6doRvhYeQrSfJKEgqfbB',
                  valid_size: '38 MB',
              },
            ]
          }
        ],
        completeDownload: {
          url: 'https://drive.google.com/open?id=1fjxU_HhxOF8f5QoXLxujYKKhc2nKkNWi',
          size: '13 GB',
          numbers: 9504
        },
        sampleDownload: {
          url: 'https://drive.google.com/open?id=14k2ZwpgTxlbNG0P6_rjwC6I1rOueWnsC',
          size: '98 MB',
          numbers: 72
        }
      }
    },
    components: {
    },
    methods: {
      goTo (section) {
        $("html, body").animate({
          scrollTop: $(`#name-${section}`).offset().top
        }, "fast");
      },
      openInNewTab (url) {
        let win = window.open(url, '_blank');
        win.focus();
      }
    }
  }
</script>

<style scoped>
  span.file_name {
    font-family: monospace, monospace;
  }
</style>
