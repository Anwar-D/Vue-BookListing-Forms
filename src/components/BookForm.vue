<template>
  <<form v-on:submit.prevent="bookSubmit(bookData)" class="" action="#" method="post">
    <input v-model="bookData.bookTitle" type="text" name="title" value="" placeholder="Book Title">
    <input v-model="bookData.bookAuthor" type="text" name="author" value="" placeholder="Book Author">
    <div>
      <div>
        <label for="finishedReading">
          Finished Reading
          <input v-model="bookData.finishedReading" type="checkbox" name="finishedReading" value="">
        </label>
      </div>
    </div>
    <div>
      <label for="borrowed">
        borrowed
        <input v-model="bookData.ownership" type="radio" id="borrowed" value="borrowed">
      </label>
      <label for="bought">
        bought
        <input v-model="bookData.ownership" type="radio" id="bought" value="bought">
      </label>
    </div>
    <button type="submit" name="button">Add Book</button>
 </form>
</template>
@@ -12,13 +30,17 @@ export default {
 props: ["books"],
 data() {
   return {
     bookTitle: "",
     bookAuthor: ""
     bookData: {
       bookTitle: "",
       bookAuthor: "",
       finishedReading: false,
       ownership: []
     }
   };
 },
 methods: {
    bookSubmit(bookTitle, bookAuthor) {
      this.$emit("addBook", bookTitle, bookAuthor);
    bookSubmit(bookData) {
      this.$emit("addBook", bookData);
    }
  }
};
