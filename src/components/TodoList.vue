<template>
  <div class="todo-list">
    <q-input
      v-model="newTodo"
      @keyup.enter="addTodo"
      placeholder="Enter a new to-do"
      outlined
    ></q-input>
    <q-btn @click="addTodo" label="Add" color="primary" class="add-btn"></q-btn>

    <q-list>
      <q-item
        v-for="(todo, index) in todos"
        :key="index"
        clickable
        v-ripple
      >
        <q-item-section>
          <span >{{ todo.text }}</span>
        </q-item-section>
        <q-item-section side>
          <q-btn
            icon="delete"
            round
            dense
            flat
            @click="removeTodo(index)"
          ></q-btn>
        </q-item-section>
      </q-item>
    </q-list>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

interface Todo {
  text: string;
}

export default defineComponent({
  name: 'TodoList',
  setup () {
    const newTodo = ref('')
    const todos = ref<Todo[]>([])

    const addTodo = () => {
      if (newTodo.value.trim()) {
        todos.value.push({ text: newTodo.value.trim() })
        newTodo.value = ''
      }
    }
    const removeTodo = (index: number) => {
      todos.value.splice(index, 1)
    }

    return {
      newTodo,
      todos,
      addTodo,
      removeTodo
    }
  }
})
</script>

<style scoped>
.todo-list {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.add-btn {
  margin: 10px 0;
}
.done {
  text-decoration: line-through;
}
</style>
