<template>
  <div>
    <v-ons-list v-for="article in articles" :key="article.id">
      <a v-bind:href="article.url" target="_blank">
      <h3>{{article.title}}</h3>
          <v-ons-list-item >
            <div class="left">
              <a v-bind:href="article.url" target="_blank">
                <img class="media-object" v-bind:src="article.urlToImage">
              </a>
            </div>
            <div class="center">
              <span class="list-item__title">{{article.author}}</span>
              <span class="list-item__subtitle">{{article.description}}</span>
            </div>
          </v-ons-list-item>
          </a>
    </v-ons-list>
  </div>
</template>

<script>
export default {
  name: 'newslist',
  props: ['source'],
  data () {
    return {
      articles: []
    }
  },
  methods: {
    updateSource: function (source) {
      this.$http.get('https://newsapi.org/v2/top-headlines?sources=' + source + '&apiKey=ac6dd81d26354c2798ef00255c4d2724')
       .then(response => {
         this.articles = response.data.articles;
       });
    }
  },
  created: function () {
    this.updateSource(this.source);
  },
  watch: {
    source: function (val) {
      this.updateSource(val);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3{
  color: beige;
  background-color: #1abc9c ;
  padding: 5px;
}
  .media-object {
    width: 150px;
    padding: 10px;
  }
  .media {
    border-top: 1px solid lightgray;
    padding-top: 20px;
  }
</style>h
