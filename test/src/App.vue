<template>
  <LayoutHeader />

  <BookList />
</template>
<script>
import LayoutHeader from './components/LayoutHeader.vue';
import BookList from './components/BookList.vue';
export default {
  components: {
    LayoutHeader,
    BookList,
  },
};
</script>
