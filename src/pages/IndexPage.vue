<template>
  <q-page class="flex flex-center">
    <TodoList />
  </q-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TodoList from 'components/TodoList.vue'

export default defineComponent({
  name: 'IndexPage',
  components: {
    TodoList
  }
})
</script>

<style scoped>
.q-page {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
</style>
