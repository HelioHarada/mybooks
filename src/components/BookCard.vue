<template>
    <div class="col-sm-2 col-md-2 col-lg-1 q-pa-sm" v-if="book.volumeInfo.imageLinks">
      <q-card class="card">
        <q-img class="book-image" v-if="book.volumeInfo.imageLinks" :src="book.volumeInfo.imageLinks.thumbnail" alt=""  />
        <q-card-section>
          {{book.volumeInfo.title}}

        </q-card-section>
      </q-card>
    </div>
</template>

<script>
export default {
  props: {
    book: {
      type: Object
    }
  },
  created () {
    console.log(this.book)
  }
}
</script>

<style lang="scss" scoped>
.card{
  max-width:150px;
  min-width: 150px;
  max-height : 310px;
  min-height : 310px
}
</style>
