<template>
  <div class="divide-y divide-gray-200 overflow-hidden rounded-lg bg-white shadow">
    <div v-if="$slots.header" class="px-4 py-5 sm:px-6">
      <slot name="header" />
    </div>
    <div v-if="$slots.content" class="px-4 py-5 sm:p-6">
      <slot name="content" />
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped></style>
