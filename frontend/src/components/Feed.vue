<template>
  <div class="feed">
    <div v-if="loading === true">
      <b>Chargement des tweets en cours…</b>
    </div>
    <div v-else>
      <ul>
        <li v-for="tweet in tweets">
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
