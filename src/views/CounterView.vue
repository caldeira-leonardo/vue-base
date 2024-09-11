<script setup>
import { useToast } from 'primevue/usetoast';
import { ref } from 'vue'


const count = ref(0);
const toast = useToast();
const show = () => {
  toast.add({
    severity: 'secondary',
    summary: 'Atenção!!!!',
    detail: 'O número ' + count.value + ' é uma dezena!',
    life: 3000
  })
}

const handlePlus = () => {
  count.value++;
  if (count.value % 10 === 0) {
    show();
  }
}

</script>

<template>
  <TheToast class="font-sans" />
  <main>
    <div class="flex flex-col gap-10 w-full h-full items-center justify-center">
      <span class="font-sans text-7xl">{{ count }}</span>
      <div class="flex flex-col gap-5">
        <div class="flex gap-10">
          <TheButton icon="pi pi-plus" @click="handlePlus" :disabled="count >= 50" />
          <TheButton icon="pi pi-minus" @click="count--" :disabled="count <= 0" />
        </div>
        <div class="">
          <TheButton class="!font-sans w-full" @click="count = 0" :disabled="count === 0">Zerar</TheButton>
        </div>
      </div>
    </div>
  </main>
</template>
