<template>
  <div class="task-item">
    <div class="task-text">
      <input type="checkbox" v-model="checked" />
      <span :class="{ done: checked }">{{ task.text }}</span>
    </div>
    <button @click="$emit('remove')">
      <i class="fas fa-trash"></i>
    </button>
  </div>
</template>

<script>
export default {
  props: ['task'],
  data() {
    return {
      checked: false
    }
  }
}
</script>

<style scoped>
.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #f9fafb;
  width: 150px;
  padding: 20px 10px;
  border-radius: 8px;
  border: 1px solid #e5e7eb;
  transition: 0.2s;
}

.task-item:hover {
  background: #f0fdf4;
}

.task-text {
  display: flex;
  align-items: center;
  gap: 8px;
  flex: 1;
}

.task-text input {
  accent-color: #42b883;
}

.task-text span.done {
  text-decoration: line-through;
  color: #9ca3af;
}

button {
  background: none;
  border: none;
  color: #e63946;
  cursor: pointer;
  font-size: 16px;
  transition: 0.2s;
}

button:hover {
  transform: scale(1.2);
  color: #b91c1c;
}
</style>
