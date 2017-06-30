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
  import Icon from 'vue-awesome/components/Icon'
  import moment from 'moment'
  export default {
    name: 'tweet',
    props: ['tweet'],
    components: {Icon},
    methods: {
      moment: function (date) { return moment(date) },
      retweet: function (id) {
        var data = new FormData()
        data.append('utilisateur', 'johndoe')
        data.append('tweet', id)
        this.$http.post('http://localhost:8080/retweet', data, {responseType: 'text'})
      }
    },
    created () {
      moment.locale('fr')
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
