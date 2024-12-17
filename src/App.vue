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
            <div v-for="task in tasks" :key="task.id" class="relative flex gap-3 py-4 px-4">
              <div class="flex h-6 shrink-0 items-center">
                <BaseCheckbox
                  :id="`task-${task.id}`"
                  v-model="completedTasks"
                  :name="`task-${task.id}`"
                  :value="task.id"
                  :checked="task.completed"
                />
              </div>
              <div class="min-w-0 flex-1 text-sm/6">
                <label
                  :for="`task-${task.id}`"
                  :class="[
                    completedTasks.includes(task.id)
                      ? 'line-through text-gray-400'
                      : 'text-gray-900',
                    'select-none font-medium ',
                  ]"
                >
                  {{ task.label }}
                </label>
              </div>
            </div>
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
import BaseCheckbox from "@/components/base/BaseCheckbox.vue";
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
