<script>
import { defineNuxtComponent } from '#app';

export default defineNuxtComponent({
  data: () => ({
    todoList: []
  }),

  computed: {
    completedItems(){
      return this.todoList.filter(item => item.completed)
    },
    remainingItems(){
      return this.todoList.filter(item => !item.completed)
    }
  },

  methods: {
    fetchTodoList() {
      fetch("http://jsonplaceholder.typicode.com/todos/")
        .then(response => response.json())
        .then(json => {
          this.todoList = json
      })
    }
  }
})


</script>

<template>
  <div>
    <img src="/todo.jpg" alt="by glenn casterns-peters" />
    <p>
      Photo by <a
        href="https://unsplash.com/@glenncarstenspeters?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Glenn
        Carstens-Peters</a> on <a
        href="https://unsplash.com/photos/RLw-UC03Gwc?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
    </p>
    <h1> Welcome to Nuxt Fundamentals</h1>
    <button @click="fetchTodoList"> Fetch Data</button>
    <p> {{ completedItems.length}} items completed | {{ remainingItems.length }} remaining items</p>
    <ul>
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" /> {{ todo.title }}
      </li>
    </ul>
  </div>
</template>