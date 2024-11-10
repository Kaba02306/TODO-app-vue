<template>
  <div class="addTask">
    タスクを追加する
    <input v-model="newTask.taskName" placeholder="タスクを入力" />
    <button @click="addTask">追加</button>
  </div>
  
  <div v-for="(task, index) in taskLists" :key="index" class="todo">
    <input type="checkbox" v-model="task.isDone" />
    <p :class="{ done: task.isDone }">{{ task.taskName }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const taskLists = ref([]);

const newTask = ref({
  taskName: '',
  isDone: false
});

const addTask = () => {
  if (newTask.value.taskName.trim()) {
    taskLists.value.push({ ...newTask.value });
    newTask.value.taskName = '';
  }
};
</script>

<style scoped>
p{
  padding: 0;
}
.addTask {
  display: flex;
  gap: 0.5rem;
}

.todo {
  display: flex;
  gap: 0.5rem;
}

.done {
  text-decoration: line-through;
  color: gray;
}
</style>
