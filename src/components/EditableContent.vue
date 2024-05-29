<!-- EditableContent.vue -->
<template>
  <div class="container">
    <h1>Catatan Harian Farrel</h1>
    <textarea v-model="inputContent" placeholder="Masukkan teks di sini..."></textarea>
    <button @click="saveContent">Save</button>
    <div v-if="savedContents.length">
      <h2>Ini Konten:</h2>
      <div v-for="(content, index) in savedContents" :key="index">
        <ContentItem 
          :content="content" 
          :index="index" 
          @update-content="updateContent" 
          @delete-content="deleteContent" 
        />
      </div>
    </div>
  </div>
</template>

<script>
import ContentItem from './ContentItem.vue';

export default {
  components: {
    ContentItem
  },
  data() {
    return {
      inputContent: '',
      savedContents: []
    };
  },
  methods: {
    saveContent() {
      if (this.inputContent.trim()) {
        this.savedContents.push(this.inputContent);
        this.inputContent = '';
      } else {
        alert('Konten tidak boleh kosong!');
      }
    },
    updateContent(index, newContent) {
      this.savedContents.splice(index, 1, newContent);
    },
    deleteContent(index) {
      this.savedContents.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 40px auto;
  padding: 20px;
  background: #f7f7f7;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  text-align: left;
}
textarea {
  width: 100%;
  height: 100px;
  padding: 10px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-family: inherit;
  font-size: 14px;
}
button {
  padding: 10px 20px;
  background-color: #28a745;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
button:hover {
  background-color: #218838;
}
h2 {
  margin-top: 40px;
  font-size: 20px;
  color: #333;
}
</style>
