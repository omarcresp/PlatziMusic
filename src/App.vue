<template lang="pug">
  #app
    img(src='src/assets/logo.png')
    h1 PlatziMusic
    select(v-model="selectedCountry")
      option(v-for="country in countrys" v-bind:value="country.value") {{ country.name }}
    spinner(v-show="loading")
    ul
      artist(v-for="artist in artists" v-bind:artist="artist" v-bind:key="artist.imbd")
</template>

<script>
import getArtist from './api'
import artist from './components/artist'
import spinner from './components/spinner'

export default {
  name: 'app',
  data () {
    return {
      artists: [],
      countrys: [
        {name: 'Argentina', value: 'argentina'},
        {name: 'Colombia', value: 'colombia'},
        {name: 'España', value: 'spain'}
      ],
      selectedCountry: 'argentina',
      loading: false
    }
  },
  methods: {
    refreshArtist() {
      const self = this
      this.loading = true
      getArtist(this.selectedCountry)
        .then(function (artist) {
          self.artists = artist
          self.loading = false
        })
    }
  },
  watch: {
    selectedCountry() {
      this.refreshArtist()
      this.artists = []
    }
  },
  components: {
    artist,
    spinner
  },
  mounted() {this.refreshArtist()}
}
</script>

<style lang="stylus">
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  h1, h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }
</style>
