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
  background: white;
  padding: 12px 15px;
  border-radius: 10px;
  border: 1px solid #e5e7eb;
  box-shadow: 0 3px 8px rgba(0, 0, 0, 0.05);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.task-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 14px rgba(0, 0, 0, 0.08);
}

.task-text {
  display: flex;
  align-items: center;
  gap: 10px;
  flex: 1;
}

.task-text input[type='checkbox'] {
  width: 18px;
  height: 18px;
  cursor: pointer;
  accent-color: #42b883;
}

.task-text span {
  font-size: 15px;
  color: #333;
  text-align: left;
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
  font-size: 18px;
  transition: transform 0.2s ease, color 0.2s ease;
}

button:hover {
  transform: scale(1.2);
  color: #b91c1c;
}
</style>
