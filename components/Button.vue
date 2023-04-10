<script lang="ts" setup>
const props = defineProps<{
  rounded: boolean;
  type: string;
}>()
</script>

<template>
  <button
    :class="[
      'button',
      type,
      {
        'rounded': rounded
      }
    ]"
  >
    <slot />
  </button>
</template>