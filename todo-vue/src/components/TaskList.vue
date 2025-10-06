<template>
  <div class="task-list" v-if="tasks.length">
    <TaskItem
      v-for="task in tasks"
      :key="task.id"
      :task="task"
      @remove="() => $emit('remove-task', task.id)"
    />
  </div>
  <p v-else class="empty">Nenhuma tarefa adicionada ainda 😴</p>
</template>

<script>
import TaskItem from './TaskItem.vue'

export default {
  props: ['tasks'],
  components: { TaskItem }
}
</script>

<style scoped>
.task-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.empty {
  color: #9ca3af;
  font-size: 14px;
  margin-top: 10px;
}
</style>
