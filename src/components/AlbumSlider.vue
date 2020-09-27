<template>
  <div class="
      album-slider
      mb-16
    "
  >
    <swiper
      effect="coverflow"
      loop
      v-if="allAlbums && allAlbums.length > 1"
      :slides-per-view="5"
      @swiper="onSwiper"
    >
      <swiper-slide
        v-for="(album, index) in allAlbums"
        :key="album.id"
      >
        <AlbumThumbnail
          :image="album.cover_image"
          :id="album.id"
          :index="index"
        />
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
import { mapState } from 'vuex'
import SwiperCore, { EffectCoverflow } from 'swiper'
import { Swiper, SwiperSlide } from 'swiper/vue'
import AlbumThumbnail from './AlbumThumbnail'

import 'swiper/swiper.scss'
import 'swiper/components/effect-coverflow/effect-coverflow.scss'

SwiperCore.use([EffectCoverflow])

export default {

  data () {
    return {
      swiperInstance: null
    }
  },

  computed: {
    ...mapState(['allAlbums', 'selectedAlbumIndex'])
  },

  watch: {
    selectedAlbumIndex (index) {
      this.updateSliderIndex(index)
    }
  },

  components: {
    Swiper,
    SwiperSlide,
    AlbumThumbnail
  },

  methods: {
    updateSliderIndex (index) {
      const newIndex = index + 3

      this.swiperInstance.slideTo(newIndex)
    },

    onSwiper (swiper) {
      this.swiperInstance = swiper
    }
  }

}
</script>

<style lang="scss">
.swiper-slide {
  opacity: .2;
  transition: opacity 500ms;
}

.swiper-slide-next + .swiper-slide {
  opacity: 1;
}
</style>
