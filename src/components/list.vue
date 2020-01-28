<template>
    <div class="d-flex justify-content-between align-items-center mb-3">
        <h1>Star Wars Films</h1>
        <select v-model="selectDate" v-on:change="getData">
            <option>Before 1980s</option>
            <option>1981 - 1990</option>
            <option>1991 - 2000</option>
            <option>2001 - 2010</option>
            <option>After 2010</option>
        </select>
    </div>
</template>

<script>
export default {
  name: 'FilmList',
  data() {
      return {
          selectDate: 'Before 1980s'
      }
  },
    methods: {
        getData(){
            this.$emit('send_date', this.selectDate)
        }
    }
}
</script>
