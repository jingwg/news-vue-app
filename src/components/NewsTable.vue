<template>
  <div id="news-table">
      <!-- for loop to display the news-->
        <div v-for="news in news_arr" :key="news.id" class = 'single-blog'>
          <a v-bind:href = "news.url"><h4>{{ news.title }}</h4></a>
          <article>{{ news.description }}</article>
        </div>
  </div>
</template>

<script>
  export default {
    name: 'news-table',
    props: {
      news_arr: Array,
    },

  }
</script>

<style scoped>
.single-blog{
    flex-grow: 1;
    flex-basis: 300px;
    text-align: center;
    padding: 30px;
    border: 1px solid #222;
    margin: 10px;
}
</style>
