<script setup>
import { ref } from "vue";

const checked = ref(false);

defineProps(['needtodo']);

</script>

<template>
  <main class="flex flex-col gap-5 items-start">
    <section class="flex flex-row items-center justify-between gap-4">
      <div class="flex flex-row gap-4">
        <TheCheckbox v-model="checked" :binary="true" />
        <label>{{ needtodo }}</label>
      </div>
      <div class="flex flex-row">
        <TheButton icon="pi pi-pencil" aria-label="edit" @click="" text />
        <TheButton icon="pi pi-trash" aria-label="delete" @click="" text />
      </div>
    </section>
  </main>
</template>

<style lang>
  .button.primary.hover.color {
    background-color: none;
  }
</style>