<template>
  <div class="feed">
    <div v-if="loading === true">
      <b>Chargement des tweets en cours…</b>
    </div>
    <div v-else>
      <ul>
        <li class="tweet" v-for="tweet in tweets">
          <tweet :tweet="tweet"/>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  import Tweet from './Tweet'
  export default {
    name: 'feed',
    components: {Tweet},
    props: ['tweets', 'loading']
  }

</script>
<style scoped>
li.tweet:first-child {
 border-top-width: 1px;
}
li.tweet {
 border-style: solid;
 border-width: 0 1px 1px 1px;
 border-color: gray;
 width: 500px;
 margin: auto;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
}
</style>
