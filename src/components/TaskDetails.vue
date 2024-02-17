<template>
  <div class="task">
    <h3>{{ task.title }}</h3>
    <div class="icons">
      <i class="material-icons" @click="handleDelete(task.id)">delete</i>
      <i class="material-icons" :class="{ active: task.isFav }" @click="handleFav(task.id)"
        >favorite</i
      >
    </div>
  </div>
</template>

<script setup>
import { useTaskStore } from '@/stores/TaskStore'

defineProps({
  task: {
    type: Object,
    required: true
  }
})

const taskStore = useTaskStore()

const handleDelete = (taskId) => {
  taskStore.deleteTask(taskId)
}

const handleFav = (taskId) => {
  taskStore.toggleFav(taskId)
}
</script>
