<script setup lang="ts">
const props = defineProps<{
  title: string;
  type: string;
}>();
</script>
<template>
  <button :class="['default', props.type]">
    <span>{{ props.title }}</span>
  </button>
</template>
<style scoped lang="scss">
.default {
  padding: 6px 12px;
  border: none;
  cursor: pointer;
  border-radius: 6px;
  transition: 0.25s;
}
.default:hover {
  filter: drop-shadow(0 0 2em var(--primary-color));
}
.primary {
  background-color: var(--primary-color);
  color: white;
}
.secondary {
  background-color: var(--secondary-color);
  color: black;
}
</style>
