<script>
  import AlgoliaAutocompleteInput from './components/AlgoliaAutocompleteInput'

  export default {
    components: {
      AlgoliaAutocompleteInput
    }
  }
</script>

<template>
  <div>
    <!-- <input type="text" v-model="query" v-on:keyup.enter="search"> -->
    <algolia-autocomplete-input></algolia-autocomplete-input>
  </div>
</template>
