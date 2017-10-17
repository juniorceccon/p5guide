<template>
  <div>
    <q-select
      v-model="agruparPor"
      float-label="Agrupar por:"
      :options="selectOptions"
    ></q-select>
    <q-list >
      <q-collapsible v-for="(grupo, key) in groupedList" group="livros" :key="key" :label="groupTitle(key, grupo)" >

          <book-detail
            v-for="(livro, index) in grupo"
            :livro="livro"
            :key="index"
            :colunas="colunas"></book-detail>

      </q-collapsible>
    </q-list>
  </div>
</template>

<script>
  import BookDetail from './BookDetail.vue'
  import {statusDesc} from './constants'
  import {QList, QItemMain, QListHeader, QSelect, QCollapsible} from 'quasar-framework'

  export default {
    props: ['lista', 'colunas'],
    data () {
      return {
        agruparPor: 'status',
        selectOptions: [{
          label: 'Local',
          value: 'obtain'
        }, {
          label: 'Status',
          value: 'status'
        }]
      }
    },
    methods: {
      groupTitle (key, lista) {
        let label = ''
        if (this.agruparPor === 'status') {
          label = `${statusDesc[key]} (${lista.length})`
        }
        else {
          label = `${key} (${lista.length})`
        }
        return label
      }
    },
    components: {
      BookDetail,
      QList,
      QListHeader,
      QSelect,
      QItemMain,
      QCollapsible
    },
    computed: {
      groupedList () {
        let grouped = {}

        for (let livro of this.lista) {
          let groupName = ''

          if (this.agruparPor === 'obtain') {
            groupName = livro[this.agruparPor].replace(/ *\(.+\)/, '')
          }
          else {
            groupName = livro[this.agruparPor]
          }

          if (!grouped[groupName]) {
            grouped[groupName] = []
          }
          grouped[groupName].push(livro)
        }

        return grouped
      }
    }
  }
</script>

<style>
</style>
