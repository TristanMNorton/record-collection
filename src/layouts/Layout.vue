<template>
  <div class="layout">
    <Header />
    <main
      class="
        flex
        h-full
      "
    >
      <AlbumList />
      <div class="dashboard">
        <AlbumSlider />
        <AlbumInfo v-if="selectedAlbumId"/>
      </div>
    </main>
  </div>
</template>

<script>
import { mapState } from 'vuex'
import AlbumList from '../components/AlbumList'
import AlbumSlider from '../components/AlbumSlider'
import AlbumInfo from '../components/AlbumInfo'
import Header from '../components/global/Header'

export default {

  components: {
    Header,
    AlbumList,
    AlbumSlider,
    AlbumInfo
  },

  computed: {
    ...mapState(['selectedAlbumId'])
  }

}
</script>

<style lang="scss">
.layout {
  background-color: #282828;
  color: #e3e2df;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
.dashboard {
  width: calc(100% - 400px);
}
</style>
