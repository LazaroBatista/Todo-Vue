<template>
  <div class="week-scroll">
    <div class="week-grid">
      <DayColumn
        v-for="day in weekDays"
        :key="day"
        :day="day"
      />
    </div>
  </div>
</template>

<script>
import DayColumn from './DayColumn.vue'

export default {
  components: { DayColumn },
  data() {
    return {
      weekDays: [
        'Segunda',
        'Terça',
        'Quarta',
        'Quinta',
        'Sexta',
        'Sábado',
        'Domingo'
      ]
    }
  }
}
</script>

<style scoped>
.week-scroll {
  overflow-x: auto;
  padding-bottom: 10px;
}

.week-grid {
  display: flex;
  justify-content: center;
  gap: 12px;
  min-width: 950px; /* garante largura mínima */
  padding: 10px;
}

@media (max-width: 900px) {
  .week-grid {
    flex-wrap: wrap;
    justify-content: center;
  }
}
</style>
