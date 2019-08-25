<template>
  <div id="app" class="container">
    <h1>Breaking News</h1>
    <input type = "text" v-model = "search" placeholder="search news title"/>
    <!-- pass data news_arr to news_table -->
    <news-table :news_arr="filteredNews" />

  </div>
</template>

<script>
import NewsTable from './components/NewsTable.vue'


export default {
  name: "app",
  components: {
    NewsTable,
  },
  data() {
    return {
      news_arr: [],
      search: ""
    }
  },
  mounted() {
    this.getNews()
  },
  methods: {
    async getNews() {
      try {
        const url = 'https://newsapi.org/v2/top-headlines?' + 'country=us&' +'apiKey=28830772d2054de4811551676b129e18'
        const response = await fetch(url)
        const data = await response.json()
        this.news_arr = data['articles']
      } catch (error) {
        console.error(error)
      }
    },

  },
  //Add search to filter the search result
  computed:{
    filteredNews: function(){
      return this.news_arr.filter((news) =>{
        return news.title.toLowerCase().includes(this.search.toLowerCase());
      });
    }
  }
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
    max-width: 680px;
  }
</style>
