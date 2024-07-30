<template>
  <tr class="table-item__table-row">
    <td>{{ title }}</td>
    <td>{{ isbn }}</td>
    <td>
      <BookButton :text="addBookmarkText" variant="secondary" @btn-clicked="changeBookmarkAdd" />
    </td>
  </tr>
</template>

<script>
import BookButton from '@/components/BookButton.vue';
export default {
  components: { BookButton },
  props: {
    title: String,
    isbn: String,
    isBookmarked: Boolean,
  },
  computed: {
    addBookmarkText() {
      return this.isBookmarked ? 'Remove Bookmark' : 'Add Bookmark';
    },
  },
  methods: {
    changeBookmarkAdd() {
      this.$emit('bookmark-clicked', this.isbn);
    },
  },
};
</script>

<style scoped>
.table-item__table td {
  padding: 12px 15px;
}
</style>
