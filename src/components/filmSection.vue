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
            <!-- <div v-for="film in info" :key="film.episode_id"> -->
                <!-- filmBefore1980s
                film1981To1990
                film1991To2000
                film2001To2010
                filmAfter2010 -->
                <!-- <template v-if="date == '1981 - 1990'">
                    <div class="col-md-4 mb-4 float-left" v-for="film in film1981To1990" :key="film.episode_id">
                        <div class="card">
                            <div class="card-body text-left">
                                <h5 class="card-title">{{film.title}}</h5>
                                <p>{{film.release_date}}</p>
                                <p class="card-text">{{film.opening_crawl}}</p>
                                <a href="#"><button class="btn btn-primary">Go Somewhere</button></a>
                            </div>
                        </div>
                    </div>
                </template>
                <template v-else-if="date == '1991 - 2000'">
                    <div class="col-md-4 mb-4 float-left" v-for="film in film1991To2000" :key="film.episode_id">
                        <div class="card">
                            <div class="card-body text-left">
                                <h5 class="card-title">{{film.title}}</h5>
                                <p>{{film.release_date}}</p>
                                <p class="card-text">{{film.opening_crawl}}</p>
                                <a href="#"><button class="btn btn-primary">Go Somewhere</button></a>
                            </div>
                        </div>
                    </div>
                </template>
                <template v-else-if="date == '2001 - 2010'">
                    <div class="col-md-4 mb-4 float-left" v-for="film in film2001To2010" :key="film.episode_id">
                        <div class="card">
                            <div class="card-body text-left">
                                <h5 class="card-title">{{film.title}}</h5>
                                <p>{{film.release_date}}</p>
                                <p class="card-text">{{film.opening_crawl}}</p>
                                <a href="#"><button class="btn btn-primary">Go Somewhere</button></a>
                            </div>
                        </div>
                    </div>
                </template>
                <template v-else-if="date == 'After 2010'">
                    <div class="col-md-4 mb-4 float-left" v-for="film in filmAfter2010" :key="film.episode_id">
                        <div class="card">
                            <div class="card-body text-left">
                                <h5 class="card-title">{{film.title}}</h5>
                                <p>{{film.release_date}}</p>
                                <p class="card-text">{{film.opening_crawl}}</p>
                                <a href="#"><button class="btn btn-primary">Go Somewhere</button></a>
                            </div>
                        </div>
                    </div>
                </template>
                <template v-else>
                    <template v-if="info">
                        <div class="col-md-4 mb-4 float-left" v-for="film in filmBefore1980s" :key="film.episode_id">
                            <div class="card">
                                <div class="card-body text-left">
                                    <h5 class="card-title">{{film.title}}</h5>
                                    <p>{{film.release_date}}</p>
                                    <p class="card-text">{{film.opening_crawl}}</p>
                                    <a href="http://localhost:8080/#"><button class="btn btn-primary">Go Somewhere</button></a>
                                </div>
                            </div>
                        </div>
                    </template>
                </template> -->
            <!-- </div> -->
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
        // filmBefore1980s: function(){
        //     return this.info.filter(film => {
        //         return film.release_date.split('-')[0] >= 0 && film.release_date.split('-')[0] <= 1980 === true
        //     })
        // },
        // film1981To1990: function(){
        //     return this.info.filter(film => {
        //         return film.release_date.split('-')[0] >= 1981 && film.release_date.split('-')[0] <= 1990 === true
        //     })
        // },
        // film1991To2000: function(){
        //     return this.info.filter(film => {
        //         return film.release_date.split('-')[0] >= 1991 && film.release_date.split('-')[0] <= 2000 === true
        //     })
        // },
        // film2001To2010: function(){
        //     return this.info.filter(film => {
        //         return film.release_date.split('-')[0] >= 2001 && film.release_date.split('-')[0] <= 2010 === true
        //     })
        // },
        // filmAfter2010: function(){
        //     return this.info.filter(film => {
        //         return film.release_date.split('-')[0] >= 2010 && film.release_date.split('-')[0] <= 9999 === true
        //     })
        // }
    }
}
</script>
