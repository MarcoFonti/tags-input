<script>
export default {
  data() {
    return {

      /* DATI  */
      isFrameworks: ['Vue.js', 'react.js', 'angular'],
      backendFrameworks: ['Laravel']
    }
  },

  /* METODO */
  methods: {

    /* METODO PER AGGIORNARE I ARRAY CON NUOVI TAGS */
    handleChange(tags) {
      this.isFrameworks = [...tags];
    },

    /* METODO PER AGGIORNARE I ARRAY CON NUOVI TAGS */
    backendChange(tags) {
      this.backendFrameworks = [...tags]
    }
  }

}

</script>

<template>
  <h1>Quali frameworks preferisci</h1>

  <!-- FRONT 'SELECTEDTAGS' = PROPS , 'CHANGE' = EMIT-->
  <div>{{ isFrameworks }}</div>
  <TagsInput :selectedTags="isFrameworks" @change="handleChange" />

  <!-- BACK 'SELECTEDTAGS' = PROPS , 'CHANGE' = EMIT -->
  <div>{{ backendFrameworks }}</div>
  <TagsInput :selectedTags="backendFrameworks" @change="backendChange" />
</template>

<style>
h1 {
  margin-top: 20px;
}
</style>
