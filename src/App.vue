<template>
  <main class="mx-auto max-w-7xl p-4 sm:p-6 lg:p-8">
    <div class="mx-auto max-w-3xl">
      <BaseCard>
        <template #content>
          <p>Hello world!</p>
        </template>
      </BaseCard>
    </div>
  </main>
</template>

<script setup lang="ts">
import BaseCard from "@/components/base/BaseCard.vue";
</script>

<style scoped></style>
