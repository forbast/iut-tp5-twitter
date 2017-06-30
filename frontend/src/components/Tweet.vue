<template>
  <div class="tweet">
    <div>
      <strong>{{tweet.auteur.nom}} {{tweet.auteur.prenom}}</strong> <span class="handle">@{{tweet.auteur.handle}}</span> - {{ moment(tweet.date).fromNow() }}
    </div>
    <div>
      <ul>
        <li class="button">
          <icon name="reply"/>
        </li>
        <a @click="retweet(tweet.id)"> <li class="button">
          <icon name="retweet"/>
          {{tweet.retweeters.length}}
        </li></a>
        <li class="button">
          <icon name="heart"/>
        </li>
        <li class="button">
          <icon name="envelope"/>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
import 'vue-awesome/icons'
import moment from 'moment'
import Icon from 'vue-awesome/components/Icon'
import Vue from 'vue'
import Resource from 'vue-resource'
Vue.use(Resource)
export default {
  created: function () {
    moment.locale('fr')
  },
  name: 'tweet',
  components: {Icon},
  props: ['tweet'],
  methods: {
    moment: function (date) {
      return moment(date)
    },
    retweet: function () {
      this.$http.get('http://localhost:8080/retweet', {params: {utilisateur: 'johndoe', tweet: this.tweet.id}, responseType: 'text'}).then(
      response => {
        this.$emit('retweeted', this.tweet.id)
      },
      response => {
        // error callback
      })
    }
  }
}
</script>


<style scoped>
li.button {
 display: inline-block;
}

a {
 color: #42b983;
}

span.handle {
 color: gray;
}

</style>
