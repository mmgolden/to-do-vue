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
                <div class="group grid size-4 grid-cols-1">
                  <input
                    :id="`task-${task.id}`"
                    v-model="completedTasks"
                    :name="`task-${task.id}`"
                    type="checkbox"
                    :value="task.id"
                    :checked="task.completed"
                    class="col-start-1 row-start-1 appearance-none rounded border border-gray-300 bg-white checked:border-indigo-600 checked:bg-indigo-600 indeterminate:border-indigo-600 indeterminate:bg-indigo-600 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:border-gray-300 disabled:bg-gray-100 disabled:checked:bg-gray-100 forced-colors:appearance-auto"
                  />
                  <svg
                    class="pointer-events-none col-start-1 row-start-1 size-3.5 self-center justify-self-center stroke-white group-has-[:disabled]:stroke-gray-950/25"
                    viewBox="0 0 14 14"
                    fill="none"
                  >
                    <path
                      class="opacity-0 group-has-[:checked]:opacity-100"
                      d="M3 8L6 11L11 3.5"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                    <path
                      class="opacity-0 group-has-[:indeterminate]:opacity-100"
                      d="M3 7H11"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                  </svg>
                </div>
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
