<template>
  <v-app color="primary">
    <v-navigation-drawer
      width="100%"
      disable-resize-watcher
      v-model="drawer"
      app
      class="d-flex justify-center"
    >
      <v-list dense>
        <div class="px-4 mb-1 d-flex align-center">
          <v-row>
            <v-col cols="12" class="d-flex justify-center">
              <v-btn
                color="white"
                :style="{fontWeight: 'bold'}"
                class="btn-app text-capitalize"
                text
              >
                <span style="font-size:24px; color:#212353;">Vacansy.</span>
              </v-btn>
            </v-col>
            <v-col cols="12" style="margin-top: -63px;" class="d-flex justify-end">
              <v-btn icon color="#212353" @click.stop="drawer = !drawer">
                <v-icon>mdi-close</v-icon>
              </v-btn>
            </v-col>
          </v-row>
        </div>
        <v-divider></v-divider>
        <v-list-item class="mt-4" link @click="setMenu('customer')">
          <v-list-item-content>
            <v-list-item-title class="d-flex justify-center">
              <span
                class="btn-app text-capitalize"
                :style="[customer ?  {fontWeight: 'bold'} : {fontWeight: 500}]"
              >Home</span>
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link @click="setMenu('merchant')">
          <v-list-item-content>
            <v-list-item-title class="d-flex justify-center">
              <span
                class="btn-app text-capitalize"
                :style="[merchant ?  {fontWeight: 'bold'} : {fontWeight: 500}]"
              >Schedule</span>
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link @click="setMenu('traffic')">
          <v-list-item-content>
            <v-list-item-title class="d-flex justify-center">
              <span
                class="btn-app text-capitalize"
                :style="[traffic ?  {fontWeight: 'bold'} : {fontWeight: 500}]"
              >Promo</span>
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link @click="setMenu('traffic')">
          <v-list-item-content>
            <v-list-item-title class="d-flex justify-center">
              <span
                class="btn-app text-capitalize"
                :style="[traffic ?  {fontWeight: 'bold'} : {fontWeight: 500}]"
              >Legal</span>
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link @click="setMenu('traffic')">
          <v-list-item-content>
            <v-list-item-title class="d-flex justify-center">
              <span
                class="btn-app text-capitalize"
                :style="[traffic ?  {fontWeight: 'bold'} : {fontWeight: 500}]"
              >Help</span>
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app height="80" color="#4657F0" class="px-12 pb-12" flat dark>
      <v-row>
        <v-col cols="auto" class="d-flex align-center">
          <a href>
            <v-btn color="white" :style="{fontWeight: 'bold'}" class="btn-app text-capitalize" text>
              <span style="font-size:24px;">Vacansy.</span>
            </v-btn>
          </a>
        </v-col>
        <v-spacer></v-spacer>
        <v-col cols="auto" class="align-center hidden-md-and-down">
          <v-btn
            color="white"
            :style="[customer ?  {fontWeight: 'bold'} : {fontWeight: 500}]"
            class="btn-app text-capitalize"
            text
            x-large
          >
            <span>Home</span>
          </v-btn>
        </v-col>
        <v-col cols="auto" class="align-center hidden-md-and-down">
          <v-menu
            :rounded="rounded"
            open-on-hover
            offset-y
            transition="slide-x-transition"
            bottom
            right
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                text
                x-large
                color="white"
                v-bind="attrs"
                v-on="on"
                :style="[merchant ?  {fontWeight: 'bold'} : {fontWeight: 500}]"
                class="btn-app text-capitalize"
              >
                Schedule
                <v-icon>mdi-chevron-down</v-icon>
              </v-btn>
            </template>
            <v-list dense>
              <v-list-item>
                <v-list-item-action>
                  <v-list-item-title>schedule 1</v-list-item-title>
                </v-list-item-action>
              </v-list-item>
              <v-list-item>
                <v-list-item-action>
                  <v-list-item-title>schedule 2</v-list-item-title>
                </v-list-item-action>
              </v-list-item>
              <v-list-item>
                <v-list-item-action>
                  <v-list-item-title>schedule 3</v-list-item-title>
                </v-list-item-action>
              </v-list-item>
            </v-list>
          </v-menu>
        </v-col>
        <v-col cols="auto" class="align-center hidden-md-and-down">
          <v-btn
            color="white"
            :style="[traffic ?  {fontWeight: 'bold'} : {fontWeight: 500}]"
            class="btn-app text-capitalize"
            text
            x-large
          >
            <span>Promo</span>
          </v-btn>
        </v-col>
        <v-col cols="auto" class="align-center hidden-md-and-down">
          <v-btn
            color="white"
            :style="[traffic ?  {fontWeight: 'bold'} : {fontWeight: 500}]"
            class="btn-app text-capitalize"
            text
            x-large
          >
            <span>Legal</span>
          </v-btn>
        </v-col>
        <v-col cols="auto" class="align-center hidden-md-and-down">
          <v-btn
            color="white"
            :style="[traffic ?  {fontWeight: 'bold'} : {fontWeight: 500}]"
            class="btn-app text-capitalize"
            text
            x-large
          >
            <span>Help</span>
          </v-btn>
        </v-col>
        <v-spacer></v-spacer>
        <v-col cols="auto" class="align-center hidden-md-and-down">
          <v-btn
            color="white"
            :style="[traffic ?  {fontWeight: 'bold'} : {fontWeight: 500}]"
            class="text-capitalize"
            x-large
            outlined
          >
            <span>Book Tickets</span>
          </v-btn>
        </v-col>
        <v-col cols="auto" class="justify-end hidden-lg-and-up">
          <v-app-bar-nav-icon color="white" @click.stop="drawer = !drawer" />
        </v-col>
      </v-row>
    </v-app-bar>

    <v-main>
      <v-row class="ma-0 pa-0">
        <v-col cols="12" class="ma-0 pa-0">
          <div class="pa-12" style="background-color:#4657F0; border-radius: 0px 0px 85px 85px;">
            <v-row>
              <v-col
                cols="12"
                sm="12"
                md="8"
                lg="8"
                class="d-flex justify-center align-center pa-8"
              >
                <v-img
                  alt="Eatmore Logo"
                  class="shrink"
                  contain
                  src="./assets/image.png"
                  width="70%"
                />
              </v-col>
              <v-col cols="12" sm="12" md="4" lg="4" class="py-8 pr-12">
                <span style="color:white; font-size:60px; font-weight:bold;">Find Your Ticket Now!</span>
                <v-text-field
                  dark
                  color="white"
                  label="Destination"
                  value="Yogyakarta, INA"
                  prepend-inner-icon="mdi-map-marker"
                ></v-text-field>
                <v-radio-group dark v-model="row" row>
                  <v-radio label="Departure" value="departure"></v-radio>
                  <v-radio label="Return" value="return"></v-radio>
                </v-radio-group>
                <v-menu
                  v-model="menu2"
                  :close-on-content-click="false"
                  :nudge-right="40"
                  transition="scale-transition"
                  offset-y
                  min-width="290px"
                >
                  <template v-slot:activator="{ on, attrs }">
                    <v-text-field
                      dark
                      v-model="date"
                      label="Departure Date"
                      prepend-inner-icon="mdi-calendar-blank-outline"
                      readonly
                      v-bind="attrs"
                      v-on="on"
                    ></v-text-field>
                  </template>
                  <v-date-picker color="#4657F0" v-model="date2" @input="menu2 = false"></v-date-picker>
                </v-menu>
                <v-row>
                  <v-col cols="8">
                    <v-dialog
                      ref="dialog"
                      v-model="modal2"
                      :return-value.sync="time"
                      persistent
                      width="290px"
                    >
                      <template v-slot:activator="{ on, attrs }">
                        <v-text-field
                          dark
                          v-model="time"
                          label="Departure Time"
                          prepend-inner-icon="mdi-clock-time-four-outline"
                          readonly
                          v-bind="attrs"
                          v-on="on"
                        ></v-text-field>
                      </template>
                      <v-time-picker color="#4657F0" v-if="modal2" v-model="time" full-width>
                        <v-spacer></v-spacer>
                        <v-btn text color="primary" @click="modal2 = false">Cancel</v-btn>
                        <v-btn text color="primary" @click="$refs.dialog.save(time)">OK</v-btn>
                      </v-time-picker>
                    </v-dialog>
                  </v-col>
                  <v-col cols="4">
                    <v-text-field
                      dark
                      color="white"
                      label="Occupant"
                      value="2 P"
                      prepend-inner-icon="mdi-account"
                    ></v-text-field>
                  </v-col>
                </v-row>
                <v-btn block x-large color="#85C633" dark class="text-capitalize">Search Tickets</v-btn>
                <!-- <h1>{{ date }}</h1>
                <v-btn @click="convert()">convert</v-btn>
                <v-btn @click="back()">back</v-btn>-->
              </v-col>
            </v-row>
            <v-row>
              <v-col
                cols="12"
                sm="12"
                md="6"
                lg="3"
                class="d-flex justify-center align-center pa-12"
              >
                <v-img src="./assets/logo1.png" width="100%" class="grey darken-4"></v-img>
              </v-col>
              <v-col
                cols="12"
                sm="12"
                md="6"
                lg="3"
                class="d-flex justify-center align-center pa-12"
              >
                <v-img src="./assets/logo2.png" width="100%" class="grey darken-4"></v-img>
              </v-col>
              <v-col
                cols="12"
                sm="12"
                md="6"
                lg="3"
                class="d-flex justify-center align-center pa-12"
              >
                <v-img src="./assets/logo3.png" width="100%" class="grey darken-4"></v-img>
              </v-col>
              <v-col
                cols="12"
                sm="12"
                md="6"
                lg="3"
                class="d-flex justify-center align-center pa-12"
              >
                <v-img src="./assets/logo4.png" width="100%" class="grey darken-4"></v-img>
              </v-col>
            </v-row>
          </div>
        </v-col>
        <v-col cols="12" class="ma-0 pa-0">
          <div class="pa-12" style="background-color:white;">
            <v-row>
              <v-col cols="12" sm="12" md="6" lg="6" class="d-flex align-center pa-8">
                <span class="footer-heading">
                  Explore Place
                  <br />Around The World
                </span>
              </v-col>
              <v-col cols="12" sm="12" md="6" lg="6" class="d-flex align-center pr-12">
                <span
                  class="footer-text"
                >The benefits of traveling are not just a one-time thing. Traveling changes you physically and psychologically</span>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12" sm="12" md="4" lg="4">
                <v-hover v-slot:default="{ hover }">
                  <v-card height="420">
                    <v-img src="./assets/4.png" :height="hover ? 200 : 420" class="grey darken-4"></v-img>
                    <v-expand-transition>
                      <div v-if="hover" style="height: 100%;">
                        <v-card-title>
                          <span class="card-title">Borobudur</span>
                        </v-card-title>
                        <v-card-text>
                          <span
                            class="footer-text"
                          >One of beauty temple you must to visit and pick the best perfect more the experience for your own interest</span>
                        </v-card-text>
                        <v-card-actions class="mt-n2">
                          <v-btn icon large color="#212353">
                            <v-icon>mdi-arrow-right</v-icon>
                          </v-btn>
                        </v-card-actions>
                      </div>
                    </v-expand-transition>
                  </v-card>
                </v-hover>
              </v-col>
              <v-col cols="12" sm="12" md="4" lg="4">
                <v-hover v-slot:default="{ hover }">
                  <v-card height="420">
                    <v-img src="./assets/5.png" :height="hover ? 200 : 420" class="grey darken-4"></v-img>
                    <v-expand-transition>
                      <div v-if="hover" style="height: 100%;">
                        <v-card-title>
                          <span class="card-title">Borobudur</span>
                        </v-card-title>
                        <v-card-text>
                          <span
                            class="footer-text"
                          >One of beauty temple you must to visit and pick the best perfect more the experience for your own interest</span>
                        </v-card-text>
                        <v-card-actions class="mt-n2">
                          <v-btn icon large color="#212353">
                            <v-icon>mdi-arrow-right</v-icon>
                          </v-btn>
                        </v-card-actions>
                      </div>
                    </v-expand-transition>
                  </v-card>
                </v-hover>
              </v-col>
              <v-col cols="12" sm="12" md="4" lg="4">
                <v-hover v-slot:default="{ hover }">
                  <v-card height="420">
                    <v-img src="./assets/6.png" :height="hover ? 200 : 420" class="grey darken-4"></v-img>
                    <v-expand-transition>
                      <div v-if="hover" style="height: 100%;">
                        <v-card-title>
                          <span class="card-title">Borobudur</span>
                        </v-card-title>
                        <v-card-text>
                          <span
                            class="footer-text"
                          >One of beauty temple you must to visit and pick the best perfect more the experience for your own interest</span>
                        </v-card-text>
                        <v-card-actions class="mt-n2">
                          <v-btn icon large color="#212353">
                            <v-icon>mdi-arrow-right</v-icon>
                          </v-btn>
                        </v-card-actions>
                      </div>
                    </v-expand-transition>
                  </v-card>
                </v-hover>
              </v-col>
            </v-row>
          </div>
        </v-col>
      </v-row>
    </v-main>

    <v-footer absolute color="white" style="padding-left:40px; padding-right: 40px;"></v-footer>
  </v-app>
</template>

<script>
import moment from 'moment'
export default {
  name: 'App',

  components: {
  },

  data: () => ({
    fab: false,
    customer: true,
    merchant: false,
    traffic: false,
    drawer: false,
    window: { 
      width: 0,
      height: 0
    },
    date: new Date().toISOString().substr(0, 10),
    date2: new Date().toISOString().substr(0, 10),
    menu: false,
    menu2: false,
    moment: moment(),
    row: null,
    time: null,
    modal2: false,
    
  }),
  mounted() {
    // this.date = moment(this.date).format('DD MMM, YYYY');
  },
  watch: {
    'window.width' (val) {
      if (val > 1261) {
        this.drawer = false
      }
    },
    date (val) {
      this.date2 = val
      this.data = moment(val).format('DD MMM, YYYY')
      // console.log(val)
    }
  },
  methods: {
    convert () {
      this.date = moment(this.date).format('DD MMM, YYYY');
    },
    back () {
      this.date = moment(this.date).format('YYYY-MM-DD');
    }
  }
};
</script>

<style lang="css">
.btn-app {
  font-family: Quicksand;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 160%;
  color: #212353;
}
.footer-heading {
  font-family: Maven Pro;
  font-style: normal;
  font-weight: bold;
  font-size: 40px;
  line-height: 130%;
  display: flex;
  align-items: center;
  color: #212353;
}
.card-title {
  font-family: Maven Pro;
  font-style: normal;
  font-weight: bold;
  font-size: 28px;
  line-height: 130%;
  display: flex;
  align-items: center;
  color: #212353;
}
.footer-heading-1 {
  font-family: Maven Pro;
  font-style: normal;
  font-weight: bold;
  font-size: 16px;
  line-height: 160%;
  color: #212353;
  display: block;
}
.footer-text {
  font-family: Quicksand;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 160%;
  color: #4b5d68;
}
</style>
