<template>
  <div class="container">
    <h1>Aplikasi Manajemen Kegiatan</h1>
    
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
      tasks: [
        { text: "Mengerjakan FreeCodeCamp", completed: false },
        { text: "Belajar JavaScript dan Framework VueJS + ViteJS", completed: false },
        { text: "Mengumpulkan UTS Sebelum Tenggat Waktu", completed: false }
      ]
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
</style>