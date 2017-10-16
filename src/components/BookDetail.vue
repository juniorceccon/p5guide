<template>
  <q-card v-if="livro" @click="teste(livro)">
    <q-card-title>
      {{livro.title}}
    </q-card-title>
    <q-card-separator />
    <q-card-main>
      <p><span class="text-bold">Title:</span> {{livro.title}} /
      <span class="text-bold">Effect:</span> {{livro.effect}} /
      <span class="text-bold">How to obtain:</span> {{livro.obtain}} /
      <span class="text-bold">Lido:</span> {{livro.lido}}</p>
    </q-card-main>
  </q-card>
</template>

<script>

import {QCard, QCardTitle, QCardSeparator, QCardMain} from 'quasar-framework'

export default {
  props: ['livro'],
  data () {
    return {}
  },
  methods: {
    teste (livro) {
      livro.lido = !livro.lido
    }
  },
  components: {QCard, QCardTitle, QCardSeparator, QCardMain}
}
</script>

<style>
</style>
