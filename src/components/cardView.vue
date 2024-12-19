<template>
  <!-- <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-3 g-4"> -->
  <div class="card-container">
      <div v-for="book in books" :key="book.title" class="card">
        <img :src="book.img_url" class="card-img" :alt="book.title" />
        <div class="card-body">
          <h5 class="card-title">{{ book.title }}</h5>
          <p class="card-text">{{ book.description }}</p>
          <p class="card-text"><small class="text-muted">By {{ book.author }}</small></p>
        </div>
      </div>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent } from "vue";
  
  export default defineComponent({
    name: "CardView",
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
  .card-container {
    display: grid;
    grid-template-columns: repeat(3, minmax(250px, 1fr));
    gap: 16px;
    margin-top: 20px;
  }
  
  .card {
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    display: flex;
    flex-direction: column;
  }
  
  .card-img {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }
  
  .card-body {
    padding: 16px;
  }
  
  .card-title {
    font-size: 1.25rem;
    font-weight: 600;
    margin-bottom: 8px;
  }
  
  .card-text {
    font-size: 1rem;
    color: #555;
  }
  
  .text-muted {
    color: #777;
  }
  </style>