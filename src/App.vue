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
              <BaseButton @click="startCreateTask"> New Task </BaseButton>
            </div>
          </div>
        </template>
        <template #content>
          <p>Hello world!</p>
        </template>
      </BaseCard>
    </div>
  </main>
</template>

<script setup lang="ts">
import BaseCard from "@/components/base/BaseCard.vue";
import BaseButton from "@/components/base/BaseButton.vue";

const startCreateTask = () => {
  console.log("create task");
};
</script>

<style scoped></style>
