<template>
  <layout />
</template>

<script>
import Layout from './layouts/Layout'
import './assets/css/tailwind.css'

export default {

  name: 'App',

  components: {
    Layout
  },

  mounted () {
    this.$store.dispatch('getAllAlbums')
  }
}
</script>
