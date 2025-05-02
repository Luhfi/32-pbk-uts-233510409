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
      <div class="task-filter">
        <h2>Daftar Kegiatan</h2>
        <label class="filter-checkbox">
          <input type="checkbox" v-model="showOnlyActive">
          <span>Tampilkan hanya yang belum selesai</span>
        </label>
      </div>
      
      <p v-if="filteredTasks.length === 0" class="empty-message">
        Tidak ada kegiatan yang ditampilkan
      </p>
      
      <ul v-else class="tasks">
        <li v-for="(task, index) in filteredTasks" :key="index" 
            class="task-item" 
            :class="{ 'task-completed': task.completed }">
          <div class="task-content">
            <input 
              type="checkbox" 
              v-model="task.completed" 
              class="task-checkbox"
            >
            <span class="task-text" :class="{ 'completed': task.completed }">{{ task.text }}</span>
          </div>
          <button @click="deleteTask(tasks.indexOf(task))" class="delete-button">×</button>
        </li>
      </ul>
      
      <div class="task-summary" v-if="tasks.length > 0">
        <p>Total: {{ tasks.length }} kegiatan | Selesai: {{ completedCount }} | Belum: {{ activeCount }}</p>
      </div>
    </div>
    
    <footer class="app-footer">
      <p>© {{ new Date().getFullYear() }} [Aplikasi Manajemen Kegiatan by: Luhfi Fahrianda]</p>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '', 
      showOnlyActive: false,
      tasks: [
        { text: "Mengerjakan FreeCodeCamp", completed: false },
        { text: "Belajar JavaScript dan Framework VueJS + ViteJS", completed: false },
        { text: "Mengumpulkan UTS Sebelum Tenggat Waktu", completed: false }
      ]
    }
  },
  computed: {
    filteredTasks() {
      if (this.showOnlyActive) {
        return this.tasks.filter(task => !task.completed);
      }
      return this.tasks;
    },
    completedCount() {
      return this.tasks.filter(task => task.completed).length;
    },
    activeCount() {
      return this.tasks.filter(task => !task.completed).length;
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
    },
    deleteTask(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>