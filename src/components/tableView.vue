<template>
  <div class="table-container">
    <table class="table">
      <thead>
        <tr>
          <th>Title</th>
          <th>Author</th>
          <th>Description</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="book in books" :key="book.title">
          <td>{{ book.title }}</td>
          <td>{{ book.author }}</td>
          <td>{{ book.description }}</td>
          <td><img :src="book.img_url" :alt="book.title"></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "TableView",
  props: {
    books: {
      type: Array as () => Array<{
        author: string;
        title: string;
        description: string;
        img_url: string;
      }>,
      required: true,
    },
  },
});
</script>

<style scoped>
.table-container {
  margin-top: 20px;
  overflow-x: auto;
}

.table {
  width: 100%;
  border-collapse: collapse;
  background-color: #fff;
}

th,
td {
  padding: 12px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

thead {
  background-color: #f7f7f7;
}

th {
  font-weight: bold;
  color: #333;
}

tbody tr:hover {
  background-color: #f1f1f1;
}

@media (max-width: 768px) {
  th, td {
    padding: 8px;
  }
}

td img {
  height: 75px;
  width: 100px;
}
</style>