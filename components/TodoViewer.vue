<script setup>
import { defineProps, ref, computed } from 'vue'

defineProps({
  title: {
    type: String,
    default: 'Welcome to Nuxt Fundamentals!'
  }
})

const todoList = ref([])

const completedItems = computed(() => {
  return todoList.value.filter(item => item.completed)
})

const remainingItems = computed(() => {
  return todoList.value.filter(item => !item.completed)
})

function fetchTodoList() {
  fetch('https://jsonplaceholder.typicode.com/todos/')
    .then(response => response.json())
    .then(json => {
      todoList.value = json
    })
}
</script>

<template>
  <BaseDisplay title="Todo Viewer" itemType="todos" v-model:itemList="todoList">

    <template v-slot:hero>
      <pre>{{ todoList }}</pre>
    </template>

    <template v-slot:metrics>
      {{ completedItems.length }} completed |
      {{ remainingItems.length }} remaining
    </template>
    
  </BaseDisplay>
</template>

<style lang="scss"></style>