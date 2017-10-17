<template>
  <!-- if you want automatic padding use "layout-padding" class -->
  <div class="layout-padding">
    <book-list :lista="book_list" ></book-list>
  </div>
</template>

<script>

import BookList from './BookList.vue'

const books = require('../../statics/books.json')

export default {
  data () {
    return {
      book_list: books
    }
  },
  components: {
    BookList
  }
}
</script>

<style>
</style>
