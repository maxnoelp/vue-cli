<template>
  <section class="table-item">
    <h2 class="table-item__hl">All Books</h2>
    <table class="table-item__table">
      <thead>
        <tr>
          <th class="table-item__table-head-name">Name</th>
          <th class="table-item__table-head--isbn">ISBN</th>
          <th class="table-item__table-head--action"></th>
        </tr>
      </thead>
      <tbody>
        <BookListRow
          v-for="book in books"
          :key="book.isbn"
          :title="book.title"
          :isbn="book.isbn"
          :isBookmarked="book?.isBookmarked"
          @bookmark-clicked="changeBookmark"
          class="table-item__table-row"
        />
      </tbody>
    </table>
  </section>
</template>

<script>
import BookListRow from './BookListRow.vue';
export default {
  components: { BookListRow },
  data() {
    return {
      books: [
        {
          title: 'Practical Rust Web Projects',
          isbn: '9781484265888',
          author: 'Shing Lyu',
          publisher: 'Apress',
          price: '$28.75',
          numPages: 256,
        },
        {
          title: 'Using WebPagetest',
          isbn: '9781491902592',
          author: 'Rick Viscomi, Andy Davies, Marcel Duran',
          publisher: "O'Reilly Media",
          price: '$25.80',
          numPages: 214,
        },
        {
          title: 'Web Scraping with Python',
          isbn: '9781491910290',
          author: 'Ryan Mitchell',
          publisher: "O'Reilly Media",
          price: '$14.00',
          numPages: 256,
        },
        {
          title: 'High Performance Mobile Web',
          isbn: '9781491912553',
          author: 'Maximiliano Firtman',
          publisher: "O'Reilly Media",
          price: '$7.00',
          numPages: 326,
        },
      ],
    };
  },
  methods: {
    changeBookmark(isbn) {
      const currentBookIndex = this.books.findIndex((book) => book.isbn === isbn);
      const currentBook = this.books[currentBookIndex];
      currentBook.isBookmarked = !currentBook.isBookmarked ? true : false;
    },
  },
};
</script>
