<template>
  <div class="app-container">
    <div class="button-container">
      <button @click="toggleView" class="toggle-btn">
        Toggle View
      </button>
    </div>

    <div class="view-container">
      <CardView v-if="!isTableView" :books="books" />
      <TableView v-else :books="books" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import CardView from './components/cardView.vue';
import TableView from './components/tableView.vue';
import books from './assets/bookdata';

export default defineComponent({
  name: 'App',
  components: {
    CardView,
    TableView,
  },
  data() {
    return {
      isTableView: false,
      books: books,
    };
  },
  methods: {
    toggleView() {
      this.isTableView = !this.isTableView;
    },
  },
});
</script>

<style scoped>
.app-container {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}

.button-container {
  margin-bottom: 20px;  
  align-content: center;
}

.toggle-btn {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.toggle-btn:hover {
  background-color: #0056b3;
}

.view-container {
  width: 100%;
  max-width: 1200px;
}
</style>