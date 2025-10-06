<template>
  <div class="day-column">
    <h2>{{ day }}</h2>

    <div class="input-area">
      <input
        v-model="newTask"
        @keyup.enter="addTask"
        type="text"
        placeholder="Adicionar tarefa..."
      />
      <button @click="addTask">+</button>
    </div>

    <div class="task-list" v-if="tasks.length">
      <TaskItem
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @remove="removeTask(task.id)"
      />
    </div>
    <p v-else class="empty">Sem tarefas hoje 😴</p>
  </div>
</template>

<script>
import TaskItem from './TaskItem.vue'

export default {
  props: ['day'],
  components: { TaskItem },
  data() {
    return {
      newTask: '',
      tasks: []
    }
  },
  mounted() {
    const saved = localStorage.getItem(`tasks-${this.day}`)
    if (saved) this.tasks = JSON.parse(saved)
  },
  watch: {
    tasks: {
      handler(newVal) {
        localStorage.setItem(`tasks-${this.day}`, JSON.stringify(newVal))
      },
      deep: true
    }
  },
  methods: {
    addTask() {
      const text = this.newTask.trim()
      if (!text) return
      this.tasks.push({ id: Date.now(), text, done: false })
      this.newTask = ''
    },
    removeTask(id) {
      this.tasks = this.tasks.filter(t => t.id !== id)
    }
  }
}
</script>

<style scoped>
.day-column {
  background: #ffffff;
  margin: 40px 0 40px 0;
  border-radius: 14px;
  padding: 50px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 140px;
  height: auto;
  transition: 0.3s;
}

.day-column:hover {
  transform: translateY(-10px);
}

h2 {
  margin-bottom: 12px;
  color: #42b883;
  font-size: 17px;
  border-bottom: 2px solid #42b883;
  padding-bottom: 5px;
}

.input-area {
  display: flex;
  gap: 6px;
  margin-bottom: 12px;
}

input {
  flex: 1;
  padding: 8px;
  width: 110px;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 14px;
  transition: 0.3s;
}

input:focus {
  border-color: #42b883;
  box-shadow: 0 0 5px rgba(66, 184, 131, 0.3);
  outline: none;
}

button {
  background: #42b883;
  color: white;
  border: none;
  border-radius: 8px;
  padding: 8px 10px;
  cursor: pointer;
  font-weight: bold;
  transition: 0.3s;
}

button:hover {
  background: #369c6e;
}

.task-list {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.empty {
  color: #9ca3af;
  font-size: 13px;
  text-align: center;
  margin-top: 20px;
}

</style>
