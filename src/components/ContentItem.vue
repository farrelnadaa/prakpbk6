<!-- ContentItem.vue -->
<template>
    <div class="content-item">
      <div v-if="!isEditing" v-html="content"></div>
      <textarea v-if="isEditing" v-model="editContent"></textarea>
      <div class="buttons">
        <button @click="isEditing ? saveEdit() : startEdit()">
          {{ isEditing ? 'Save' : 'Edit' }}
        </button>
        <button @click="deleteContent">Delete</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      content: {
        type: String,
        required: true
      },
      index: {
        type: Number,
        required: true
      }
    },
    data() {
      return {
        isEditing: false,
        editContent: this.content
      };
    },
    methods: {
      startEdit() {
        this.isEditing = true;
      },
      saveEdit() {
        this.isEditing = false;
        this.$emit('update-content', this.index, this.editContent);
      },
      deleteContent() {
        this.$emit('delete-content', this.index);
      }
    }
  };
  </script>
  
  <style scoped>
  .content-item {
    background: #fff;
    padding: 20px;
    margin-bottom: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: box-shadow 0.3s ease;
  }
  .content-item:hover {
    box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
  }
  textarea {
    width: 100%;
    height: 100px;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-family: inherit;
    font-size: 14px;
  }
  .buttons {
    display: flex;
    gap: 10px;
  }
  button {
    padding: 10px 15px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  button:hover {
    background-color: #0056b3;
  }
  button + button {
    background-color: #ff4d4d;
  }
  button + button:hover {
    background-color: #cc0000;
  }
  </style>
  