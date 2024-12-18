<template>
  <main class="mx-auto max-w-7xl p-4 sm:p-6 lg:p-8">
    <div class="mx-auto max-w-3xl">
      <BaseCard>
        <template #header>
          <div class="-ml-4 -mt-2 flex flex-wrap items-center justify-between sm:flex-nowrap">
            <div class="ml-4 mt-2">
              <h3 class="text-base font-semibold text-gray-900">Task List</h3>
            </div>
            <div class="ml-4 mt-2 shrink-0">
              <BaseButton @click="handleClick"> New Task </BaseButton>
            </div>
          </div>
        </template>
        <template #content>
          <div class="divide-y divide-gray-200 border-b border-gray-200">
            <TaskListItem
              v-for="task in tasks"
              :key="task.id"
              :task="task"
              v-model="completedTasks"
            />
          </div>
        </template>
      </BaseCard>
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref } from "vue";
import BaseCard from "@/components/base/BaseCard.vue";
import BaseButton from "@/components/base/BaseButton.vue";
import TaskListItem from "@/components/task/TaskListItem.vue";
import tasksData from "./tasks.json";
import type { Task } from "@/types";

const tasks = ref<Task[]>(tasksData);

const completedTasks = ref<Array<number>>(
  tasks.value.filter((task) => task.completed).map((task) => task.id),
);

const handleClick = () => {
  console.log("new task");
};
</script>

<style scoped></style>
