<template>
    <div class="jumbotron">
      <select class="form-control" v-on:change="sourceChanged">
        <option value="">S'il vous plait choisisez une option</option>
        <option v-for="source in sources" v-bind:value="source.id">{{source.name}}</option>
      </select>
      <br>
      <div v-if="source">
        <!-- <h6>{{source.description}}</h6> -->
        <a v-bind:href="source.url" class="btn btn-primary" target="_blank">Aller vers {{source.name}} Website</a>
      </div>
    </div>
</template>

<script>
export default {
  name: 'sourceselection',
  data () {
    return {
      sources: [],
      source: ''
    }
  },
  methods: {
    sourceChanged: function(e) {
     for (var i=0; i<this.sources.length; i++) {
       if (this.sources[i].id == e.target.value) {
         this.source = this.sources[i];
       }
     }
     this.$emit('sourceChanged', e.target.value);
    }
  },
  created: function () {
    this.$http.get('https://newsapi.org/v2/sources?language=fr&apiKey=ac6dd81d26354c2798ef00255c4d2724')
      .then(response => {
        this.sources = response.data.sources;
      });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
