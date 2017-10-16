<template>
  <div>
    <q-list v-for="(grupo, key) in grupos" :key="key">
      <q-list-header>{{key}}</q-list-header>
      <book-detail v-for="livro in grupo" :livro="livro" :key="livro.title" @click="teste(livro)" />
    </q-list>
  </div>
</template>

<script>

import BookDetail from './BookDetail.vue'
import {QList, QListHeader} from 'quasar-framework'

export default {
  props: ['lista', 'groupby'],
  data () {
    return {}
  },
  components: {
    BookDetail,
    QList,
    QListHeader
  },
  methods: {
    teste (livro) {
      console.log(livro)
    }
  },
  computed: {
    grupos () {
      let grupos = {}

      for (let item of this.lista) {
        let key = item.obtain.replace(/ \(.+\) */, '')

        if (!grupos[key]) {
          grupos[key] = []
        }

        grupos[key].push(item)
      }

      return grupos
    }
  }
}
</script>

<style>
</style>
