<template>
  <q-page class="">
    <div class="row justify-center">
      <h3>Books</h3>
    </div>
    <div class="row justify-center">
      <!-- input Busca -->
      <q-input
        color="primary"
        class="input-busca q-ma-sm q-mb-lg"
        @keyup.enter="getBooks(text)"
        label-color="primary"
        outlined v-model="text"
        label="Pesquisar"
        :loading="loadingState"
       >
        <template v-slot:append v-if="!loadingState">
          <q-icon name="search" color="primary" />
        </template>
      </q-input>

    </div>
    <div class="row justify-center">
      <book-card v-for="(item ,index) in books" :key="index"  :book="item" />
    </div>
  </q-page>
</template>

<script>
import BookCard from 'components/BookCard'

export default {
  name: 'PageIndex',
  components: {
    'book-card': BookCard
  },
  data () {
    return {
      books: '',
      key: 'AIzaSyCTlKUCIb45DsQ2Vw4Ul1K5qInFGatb-hc',
      text: '',
      loadingState: false
    }
  },
  methods: {
    async getBooks (book) {
      try {
        console.log(book)
        this.loadingState = true
        if (book === '' || book === 'undefined' || book === null) {
          console.log('vazio')
          this.books = ''
        } else {
          const data = await this.$axios.get('https://www.googleapis.com/books/v1/volumes?q=' + book, { params: { startIndex: 1, maxResults: 40 } })
          this.books = data.data.items
        }

        // console.log(this.books)
      } catch (error) {
        console.log(error)
      } finally {
        this.loadingState = false
      }
    }
  }
}
</script>
<style lang="scss" scoped>
.input-busca{
  width: 400px;
}
</style>
