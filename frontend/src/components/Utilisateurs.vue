<template>
  <div class="utilisateur">
    <select @change="onChange($event.target.value)">
      <option disabled value="">Choisissez un utilisateur ...</option>
      <option v-for="utilisateur in utilisateurs" :value="utilisateur.handle">
        {{ utilisateur.prenom }} {{ utilisateur.nom }}
      </option>
    </select>
  </div>
</template>
<script>
  export default {
    name: 'utilisateur',
    props: [ 'utilisateurs' ]
  }
</script>
<style scoped>
</style>

