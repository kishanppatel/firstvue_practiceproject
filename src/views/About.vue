<template>
  <div class="about container my-5">
    <!-- <h1>This is an about page</h1> -->
    <FilmList v-on:send_date="dateSelected" style="display:none !important;"/>
    {{episode_number}}
    <div class="row text-left">
      <template v-if="info">
        <div class="col mb-4 float-left" v-for="film in filmData" :key="film.episode_id">
          <h1 class="title">{{film.title}}</h1><br>
          <p>
            {{ moment(film.release_date).format('MMMM Do YYYY') }}
          </p>
          <p class="card-text">{{film.opening_crawl}}</p>
          <button class="btn btn-primary">
            <router-link to="/" style="color:#fff;">Back to Home</router-link>
          </button>
        </div>
      </template>
    </div>
  </div>
</template>
<script>
import FilmList from '@/components/list.vue'

const moment = require('moment')
const axios = require("axios").default;

export default {
  name: "about",
  components: {
      FilmList
      },
  props: ["selectDate"],
  data() {
    return {
      date: "",
      info: "",
      episode_number: window.location.pathname.split('/').pop(),
    };
  },
  mounted() {
    axios
      .get("https://swapi.co/api/films/?format=json")
      .then(response => (this.info = response.data.results));
  },
  methods: {
    dateSelected(sDate) {
      this.date = sDate
    },
    moment: function (date) {
      return moment(date);
    },
  },
  computed: {
    filmData: function() {
      return this.info.filter(film => {
        return this.episode_number == film.episode_id;
      });
      
  //     if (this.date == "1981 - 1990") {
  //       return this.info.filter(film => {
  //         return moment(film.release_date).isBetween(
  //           "1981-01-01",
  //           "1990-12-31"
  //         );
  //       });
  //     } else if (this.date == "1991 - 2000") {
  //       return this.info.filter(film => {
  //         return moment(film.release_date).isBetween(
  //           "1991-01-01",
  //           "2000-12-31"
  //         );
  //       });
  //     } else if (this.date == "2001 - 2010") {
  //       return this.info.filter(film => {
  //         return moment(film.release_date).isBetween(
  //           "2001-01-01",
  //           "2010-12-31"
  //         );
  //       });
  //     } else if (this.date == "After 2010") {
  //       return this.info.filter(film => {
  //         return moment(film.release_date).isBetween(
  //           "2010-01-01",
  //           "9999-12-31"
  //         );
  //       });
  //     } else {
  //       return this.info.filter(film => {
  //         return moment(film.release_date).isBetween(
  //           "0001-01-01",
  //           "1980-12-31"
  //         );
  //       });
  //     }
    }
  }
};
</script>
