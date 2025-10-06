<template>
  <div class="app">
    <h1>📝 Lista de Tarefas</h1>

    <div class="input-area">
      <input
        v-model="newTask"
        type="text"
        placeholder="Digite uma nova tarefa..."
        @keyup.enter="addTask"
      />
      <button @click="addTask">Adicionar</button>
    </div>

    <TaskList
      :tasks="tasks"
      @remove-task="removeTask"
    />
  </div>
</template>

<script>
import TaskList from './components/TaskList.vue'

export default {
  components: { TaskList },
  data() {
    return {
      newTask: '',
      tasks: []
    }
  },
  methods: {
    addTask() {
      const texto = this.newTask.trim()
      if (texto === '') return
      this.tasks.push({ id: Date.now(), text: texto })
      this.newTask = ''
    },
    removeTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id)
    }
  }
}
</script>

<style scoped>
.app {
  max-width: 550px;
  margin: 60px auto;
  text-align: center;
  font-family: 'Poppins', sans-serif;
  background: #f9fafb;
  border-radius: 16px;
  padding: 30px;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);
}

h1 {
  color: #2b2b2b;
  margin-bottom: 25px;
}

.input-area {
  display: flex;
  justify-content: space-between;
  gap: 10px;
  margin-bottom: 25px;
}

input {
  flex: 1;
  padding: 12px;
  border-radius: 8px;
  border: 1px solid #d1d5db;
  transition: all 0.3s ease;
  font-size: 15px;
}

input:focus {
  outline: none;
  border-color: #42b883;
  box-shadow: 0 0 5px rgba(66, 184, 131, 0.5);
}

button {
  background-color: #42b883;
  border: none;
  color: white;
  padding: 12px 18px;
  cursor: pointer;
  border-radius: 8px;
  font-weight: 600;
  transition: all 0.3s ease;
}

button:hover {
  background-color: #369c6e;
  transform: scale(1.05);
}
</style>
