<template>
    <div class="hello container my-5">
        <FilmList v-on:send_date="dateSelected"/>
        <div class="row">
            <template v-if="info">
                <div class="col-md-4 mb-4 float-left" v-for="film in filmData" :key="film.episode_id">
                    <div class="card">
                        <div class="card-body text-left">
                            <h5 class="card-title">{{film.title}}</h5>
                            <p>{{film.release_date}}</p>
                            <p class="card-text">{{film.opening_crawl}}</p>
                            <button class="btn btn-primary">                
                                <router-link :to="{path:'/film/'+film.episode_id}" style="color: #fff;">Go Somewhere</router-link>
                            </button>
                        </div>
                    </div>
                </div>
            </template>
        </div>
    </div>
</template>

<script>
import FilmList from 'G:/javascript/Vue cli/star-wars-api/src/components/list.vue'

const moment = require('moment')
const axios = require('axios').default
export default {
    name: 'FilmSection',
    components: {
        FilmList
        },
    props: ['selectDate'],
    data () {
        return {
            date: '',
            info: ''
        }
    },
    mounted () {
        axios
        .get('https://swapi.co/api/films/?format=json')
        .then(response => (this.info = response.data.results))
    },
    methods: {
        dateSelected(sDate){
            this.date = sDate
        }
    },
    computed: {
            filmData: function(){
                if(this.date == '1981 - 1990'){
                    return this.info.filter(film => {
                        return moment(film.release_date).isBetween('1981-01-01', '1990-12-31');
                    })
                }else if(this.date == '1991 - 2000'){
                    return this.info.filter(film => {
                        return moment(film.release_date).isBetween('1991-01-01', '2000-12-31');
                    })
                }else if(this.date == '2001 - 2010'){
                    return this.info.filter(film => {
                        return moment(film.release_date).isBetween('2001-01-01', '2010-12-31');
                    })
                }else if(this.date == 'After 2010'){
                    return this.info.filter(film => {
                        return moment(film.release_date).isBetween('2010-01-01', '9999-12-31');
                    })
                }else{
                    return this.info.filter(film => {
                        return moment(film.release_date).isBetween('0001-01-01', '1980-12-31');
                    })
                }
                
            }
    }
}
</script>
