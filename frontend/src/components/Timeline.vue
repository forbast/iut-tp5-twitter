<template>
  <div>
    <h1>coucouc</h1>
    <feed :tweets="tweets" :loading="loading"/>
  </div>
</template>


<script>
import Vue from 'vue'
import Resource from 'vue-resource'
Vue.use(Resource)
import Feed from './Feed'
export default {
  name: 'hello',
  data () {
    return {
      tweets: [],
      loading: true
    }
  },
  components: {Feed},
  methods: {
    fetchTweets: function () {
      this.$http.get('http://localhost:8080/list').then(response => {
        this.tweets = response.body
        this.loading = false
      }, response => {
      })
    }
  },
  created () {
    this.fetchTweets()
  }
}
</script>

<style scoped>
</style>
