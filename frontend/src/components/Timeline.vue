<template>
  <div>
    <h1>coucouc</h1>
    <ul>
      <li>
        <router-link to="/timeline">Timeline</router-link>
      </li>
    </ul>
    <ul>
      <li v-for="tweet in tweets">
        <tweet :tweet="tweet"/>
      </li>
    </ul>
  </div>
</template>


<script>
var tweet1 = {auteur: 'test1', contenu: 'test1234'}
var tweet2 = {auteur: 'test2', contenu: 'test234'}
var tweet3 = {auteur: 'test3', contenu: 'test34'}
import Tweet from './Tweet'
export default {
  name: 'hello',
  data () {
    return {
      tweets: [tweet1, tweet2, tweet3]
    }
  },
  components: {Tweet}
}

</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
}


</style>
