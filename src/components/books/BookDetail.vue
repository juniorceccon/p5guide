<template>
  <q-card v-if="livro" @click="teste(livro)">
    <q-card-title>
      {{livro.title}}
    </q-card-title>
    <q-card-separator ></q-card-separator>
    <q-card-main>
        <p v-for="(coluna, key) in colunas" :key="key">
          {{coluna}}: {{ getLivroProp(key) }}
        </p>
    </q-card-main>
    <q-card-separator ></q-card-separator>
    <q-card-actions>
      <q-radio v-for="(desc, key) in statusDesc" v-model="livro.status" :key="key" :val="key" :label="desc" style="margin-left: 10px"></q-radio>
    </q-card-actions>
  </q-card>
</template>

<script>

import {QCard, QCardTitle, QCardSeparator, QCardMain, QItem, QCardActions, QRadio} from 'quasar-framework'

import {statusDesc} from './constants'

export default {
  props: ['livro'],
  data () {
    return {
      colunas: {
        title: 'Título',
        obtain: 'Onde conseguir'
      },
      statusDesc: statusDesc
    }
  },
  methods: {
    teste (livro) {
      livro.lido = !livro.lido
    },
    getLivroProp (prop) {
      return this.livro[prop]
    }
  },
  components: {QCard, QCardTitle, QCardSeparator, QCardMain, QItem, QCardActions, QRadio}
}
</script>

<style>
</style>
