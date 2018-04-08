<template>
  <div class="">
    <SourceSelection v-on:sourceChanged="sourceChanged"></SourceSelection>
    <Newslist v-bind:source="source"></Newslist>
  </div>
</template>

<script>
import Newslist from './Newslist'
import SourceSelection from './SourceSelection'

export default {
  name: 'app',
  components: {
    Newslist,
    SourceSelection
  },
  data () {
    return {
      source: ""
    }
  },
  methods: {
    sourceChanged: function (source) {
      this.source = source;
    },
    goTo (url) {
      window.open(url, '_blank')
    }
  }
}
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

ons-list-title {
  text-transform: none;
}

ons-list-title:not(:first-of-type) {
  margin-top: 30px;
}

ons-card {
  text-align: center;
}

ons-list-item, ons-card {
  cursor: pointer;
}
</style>
