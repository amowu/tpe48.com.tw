<style>
  .algolia-autocomplete {
    width: 100%;
  }
  .algolia-autocomplete .aa-input, .algolia-autocomplete .aa-hint {
    width: 100%;
  }
  .algolia-autocomplete .aa-hint {
    color: #999;
  }
  .algolia-autocomplete .aa-dropdown-menu {
    width: 100%;
    background-color: #fff;
    border: 1px solid #999;
    border-top: none;
  }
  .algolia-autocomplete .aa-dropdown-menu .aa-suggestion {
    cursor: pointer;
    padding: 5px 4px;
  }
  .algolia-autocomplete .aa-dropdown-menu .aa-suggestion.aa-cursor {
    background-color: #B2D7FF;
  }
  .algolia-autocomplete .aa-dropdown-menu .aa-suggestion em {
    font-weight: bold;
    font-style: normal;
  }
</style>

<script>
  import algoliasearch from 'algoliasearch/lite'
  import autocomplete from 'autocomplete.js'

  const client = algoliasearch('HWJ6NH4DL3', '486c67bf5d6e09cc43816091e4bce882')
  const index = client.initIndex('AKB48')
  let search

  export default {
    ready () {
      search = autocomplete('#search-input', {
        autoselect: true,
        hint: true,
        debug: false,
        openOnFocus: false
      }, [{
        source: autocomplete.sources.hits(index, { hitsPerPage: 5 }),
        displayKey: 'full_name_ja'
      }]).on('autocomplete:selected', function (event, suggestion, dataset) {
        console.log(suggestion, dataset)
      })
    },
    beforeDestroy () {
      search.destroy()
      client.destroy()
    }
  }
</script>

<template>
  <div>
    <input type="text" id="search-input">
  </div>
</template>
