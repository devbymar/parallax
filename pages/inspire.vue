<template>
  <div class="books-container">
    <div v-for="book in books" :key="book.id" class="row flex justify-between">
      <carComp20 class="col-5"
        :title="book.title"
        :price="book.price"
        :isbn="book.isbn13"
        :description="book.subtitle"
        :cover_image="book.image"
        :url="book.url"
      />
    </div>
  </div>
</template>

<script setup>
import axios from 'axios'
import {ref, onMounted} from 'vue'
// import card from '../components/cardComp.vue'
import carComp20 from '../components/cardComp2.0.vue'

const books = ref([])
const getBooks = async () => {
  const resp = await axios.get('https://api.itbook.store/1.0/search/mongodb')
  books.value = resp.data.books
}

onMounted(() => {
  getBooks()
})
</script>

<style scoped>
.books-container {
  padding-left: 25px;
}
</style>
