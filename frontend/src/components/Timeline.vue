<template>
  <div>
    <h1>coucouc</h1>
    <ul>
      <li>
        <router-link to="/timeline">Timeline</router-link>
      </li>
    </ul>
    <ul>
      <li v-for="tweet in tweets">{{tweet}}</li>
    </ul>
  </div>
</template>


<script>
export default {
  name: 'hello',
  data () {
    return {
      tweets: ['tweet 1', 'tweet 2', 'tweet 3']
    }
  }
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
