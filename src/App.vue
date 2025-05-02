<template>
  <div class="container">
    <h1>Aplikasi Manajemen Kegiatan</h1>
    
    <div class="add-task">
      <input 
        type="text" 
        v-model="newTask" 
        @keyup.enter="addTask"
        placeholder="Tambahkan kegiatan baru..."
        class="task-input"
      >
      <button @click="addTask" class="add-button">Tambah</button>
    </div>
    
    <div class="task-list">
      <h2>Daftar Kegiatan</h2>
      
      <p v-if="tasks.length === 0" class="empty-message">
        Belum ada kegiatan yang ditambahkan
      </p>
      
      <ul v-else class="tasks">
        <li v-for="(task, index) in tasks" :key="index" class="task-item">
          {{ task.text }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '', 
      tasks: [
        { text: "Mengerjakan FreeCodeCamp", completed: false },
        { text: "Belajar JavaScript dan Framework VueJS + ViteJS", completed: false },
        { text: "Mengumpulkan UTS Sebelum Tenggat Waktu", completed: false }
      ]
    }
  },
  methods: {
    addTask() {
      if (this.newTask.trim() === '') return 
      
      this.tasks.push({
        text: this.newTask,
        completed: false
      })
      
      this.newTask = '' 
    }
  }
}
</script>

<style>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  text-align: center;
  color: #4a6fa5;
}

h2 {
  margin-top: 20px;
  color: #166088;
}

.empty-message {
  font-style: italic;
  color: #888;
  text-align: center;
  padding: 20px;
  background-color: #f7f7f7;
  border-radius: 5px;
}

.tasks {
  list-style-type: none;
  padding: 0;
}

.task-item {
  padding: 12px 15px;
  background-color: #f7f9fb;
  border-left: 3px solid #4cb5ae;
  margin-bottom: 8px;
  border-radius: 5px;
}

.add-task {
  display: flex;
  margin-bottom: 20px;
  gap: 10px;
}

.task-input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 16px;
}

.add-button {
  padding: 10px 20px;
  background-color: #4cb5ae;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
}

.add-button:hover {
  background-color: #3da89f;
}
</style>