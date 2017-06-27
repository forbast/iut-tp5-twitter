<template>
    <div class="tweet">
      {{tweet.auteur.nom}} {{tweet.auteur.prenom}} | {{tweet.auteur.handle}}
    </div>
</template>
<script>
  export default {
    name: 'tweet',
    props: ['tweet']
  }
</script>

