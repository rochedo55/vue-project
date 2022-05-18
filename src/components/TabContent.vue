<template>
  <div class="contents">
    <button className="btn btn-primary" @click.prevent="$emit('onChange', index)">
      {{ text }}
    </button>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  index: string[];
  text: string[];
}>();
defineEmits<{(e: "onChange", val: number): void}>();
</script>
