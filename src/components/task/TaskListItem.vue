<template>
  <div class="relative flex gap-3 py-4 px-4">
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
          completedTasks.includes(task.id) ? 'line-through text-gray-400' : 'text-gray-900',
          'select-none font-medium ',
        ]"
      >
        {{ task.label }}
      </label>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from "vue";
import BaseCheckbox from "@/components/base/BaseCheckbox.vue";
import type { Task } from "@/types";

const props = defineProps<{
  task: Task;
  modelValue: Array<number>;
}>();

const emit = defineEmits(["update:modelValue"]);

const completedTasks = computed({
  get() {
    return props.modelValue;
  },
  set(value) {
    emit("update:modelValue", value);
  },
});
</script>

<style scoped></style>
