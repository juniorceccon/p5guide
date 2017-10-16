<template>
  <!-- if you want automatic padding use "layout-padding" class -->
  <div class="layout-padding">
    <h1>Lido</h1>
    <book-list :lista="lido"/>
    <h1>Não lido</h1>
    <book-list :lista="naolido"/>
  </div>
</template>

<script>

import BookList from './BookList.vue'
import books from '../statics/books.json'

for (let book of books) {
  book.lido = false
}

export default {
  data () {
    return {
      books_list: books
    }
  },
  components: {
    BookList
  },
  computed: {
    lido () {
      return books.filter(l => l.lido)
    },
    naolido () {
      return books.filter(l => !l.lido)
    }
  }

}
</script>

<style>
</style>
