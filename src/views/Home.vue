<template>
  <div class="home">
    <SliderImage/>
    <FilmSection/>
    <ImageSection/>
  </div>
</template>

<script>
// @ is an alias to /src
import FilmSection from '@/components/filmSection.vue'
import ImageSection from '@/components/ImageSection.vue'
import SliderImage from '@/components/SliderImage.vue'

export default {
  name: 'home',
  components: {
    FilmSection,
    ImageSection,
    SliderImage,
  }
}
</script>
