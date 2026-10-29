<template>
  <ul class="book-list">
    <!-- 1. v-for + :key, instanciation de BookCard -->
    <BookCard
      v-for="book in books"
      :book="book"
      :key="book.id"
      @toggle-fav="$emit('toggle-fav', $event)"
    >
      <!-- 4. Contenu injecté dans le slot nommé "actions" -->
      <template #actions>
        <span class="hint">📖 À lire</span>
      </template>
    </BookCard>
  </ul>
</template>

<script>
import BookCard from './BookCard.vue'

export default {
  name: 'BookList',
  components: { BookCard },
  props: {
    books: {
      type: Array,
      required: true
    }
  },
  emits: ['toggle-fav']
}
</script>

<style scoped>
.book-list {
  list-style: none;
  padding: 0;
}
.hint {
  color: #666;
  font-size: 0.9rem;
}
</style>
