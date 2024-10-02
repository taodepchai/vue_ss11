<template>
  <div>
    <h1>bt1</h1>
    <B1></B1>
    <h1>bt2</h1>
    <B2></B2>
    <h1>bt3</h1>
    <B3></B3>
    <h1>bt4</h1>
    <B4parent></B4parent>
    <h1>bt5</h1>
    <B5Parent></B5Parent>
    <h1>bt6</h1>
    <B6></B6>
    <h1>bt7</h1>
    <B7></B7>
    <h1>bt8</h1>
    <B8></B8>
    <h1>bt9</h1>
    <B9></B9>
    <h1>bt10</h1>
    <B10></B10>
    <h1>ss12</h1>
    <div class="app-container">
      <h1>Quản lý mượn trả sách</h1>
      <button @click="openAddForm" class="add-button">Thêm thông tin</button>

      <BookForm
        v-if="isFormVisible"
        @save="handleSave"
        @close="closeForm"
        :editData="currentEditData"
      />

      <BookList
        :books="books"
        @delete="openDeleteModal"
        @edit="openEditForm"
        @statusChange="handleStatusChange"
      />

      <Modal
        v-if="isDeleteModalVisible"
        @confirm="confirmDelete"
        @cancel="closeDeleteModal"
      />
    </div>
  </div>
</template>

<script setup>
import B1 from "./components/ss11/B1.vue";
import B2 from "./components/ss11/B2.vue";
import B3 from "./components/ss11/B3.vue";
import B4parent from "./components/ss11/B4parent.vue";
import B5Parent from "./components/ss11/B5Parent.vue";
import B6 from "./components/ss11/B6.vue";
import B7 from "./components/ss11/B7.vue";
import B8 from "./components/ss11/B8.vue";
import B9 from "./components/ss11/B9.vue";
import B10 from "./components/ss11/B10.vue";

import { ref } from "vue";
import BookList from "./components/ss12/BookList.vue";
import BookForm from "./components/ss12/BookForm.vue";
import Modal from "./components/ss12/Modal.vue";

const books = ref(JSON.parse(localStorage.getItem("books")) || []);
const isFormVisible = ref(false);
const isDeleteModalVisible = ref(false);
const currentEditData = ref(null);
const bookToDelete = ref(null);

const openAddForm = () => {
  currentEditData.value = null;
  isFormVisible.value = true;
};

const openEditForm = (book) => {
  currentEditData.value = book;
  isFormVisible.value = true;
};

const handleSave = (book) => {
  if (currentEditData.value) {
    const index = books.value.findIndex((item) => item.id === book.id);
    books.value.splice(index, 1, book);
  } else {
    book.id = Date.now();
    books.value.push(book);
  }
  localStorage.setItem("books", JSON.stringify(books.value));
  isFormVisible.value = false;
};

const handleStatusChange = (bookId, status) => {
  const book = books.value.find((item) => item.id === bookId);
  if (book) {
    book.status = status;
    localStorage.setItem("books", JSON.stringify(books.value));
  }
};

const openDeleteModal = (book) => {
  bookToDelete.value = book;
  isDeleteModalVisible.value = true;
};

const confirmDelete = () => {
  books.value = books.value.filter((book) => book.id !== bookToDelete.value.id);
  localStorage.setItem("books", JSON.stringify(books.value));
  closeDeleteModal();
};

const closeDeleteModal = () => {
  isDeleteModalVisible.value = false;
};

const closeForm = () => {
  isFormVisible.value = false;
};
</script>

<style scoped></style>
