<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  img: {
    default: "https://placehold.co/600x600"
  },
  name: {
    default: "John Doe"
  },
  role: {
    default: "Software Engineer"
  }
})
</script>


<template>
    <div class="text-2xl flex flex-col items-center gap-2 w-40 z-10">
        <img :src="props.img" class="rounded-full w-40 h-40 object-cover shadow-lg border-2 border-purple-800" />
        <div class="text-2xl">
            <slot />
        </div>
        <div class="text-xl font-bold text-purple-300">
            {{ props.name }}
        </div>
        <div class="text-sm text-purple-400">
            <div v-for="(role, index) in props.role.split('+')" :key="index">
                {{ role.trim() }}
            </div>
        </div>
    </div>
</template>