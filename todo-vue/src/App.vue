<template>
  <div class="app">
    <h1>📅 Planejador Semanal</h1>
    <WeekPlanner />
  </div>
</template>

<script>
import WeekPlanner from './components/WeekPlanner.vue'

export default {
  components: { WeekPlanner }
}
</script>

<style scoped>
.app {
  max-width: 1100px;
  margin: 40px auto;
  padding: 25px;
  font-family: 'Poppins', sans-serif;
  text-align: center;
  background: #f9fafb;
  border-radius: 20px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  overflow-x: auto;
}
h1 {
  margin-bottom: 25px;
  color: #222;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 8px;
}
</style>
