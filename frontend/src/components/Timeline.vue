<template>
  <div>
    <utilisateurs :utilisateurs="utilisateurs"/>
    <h1>coucouc</h1>
    <feed :tweets="tweets" :loading="loading" @retweeted="retweet"/>
  </div>
</template>


<script>
import Utilisateurs from './Utilisateurs'
import Vue from 'vue'
import Resource from 'vue-resource'
Vue.use(Resource)
import Feed from './Feed'
export default {
  name: 'hello',
  data () {
    return {
      tweets: [],
      loading: true,
      utilisateurs: []
    }
  },
  components: {Feed, Utilisateurs},

  methods: {
    retweet: function (id) {
      var tweet = this.tweets.find(tweet => tweet.id === id)
      tweet.retweeters.push({handle: 'snoopdog'})
    },
    fetchTweets: function () {
      this.$http.get('http://localhost:8080/list').then(response => {
        this.tweets = response.body
        this.loading = false
      }, response => {
      })
    },
    fetchUtilisateurs: function () {
      this.$http.get('http://localhost:8080/utilisateurs').then(response => {
        this.utilisateurs = response.body
      }, response => {
      })
    }
  },

  created () {
    this.fetchUtilisateurs()
    this.fetchTweets()
  }
}
</script>

<style scoped>
</style>
