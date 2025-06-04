<template>
    <div>
        <img src="../assets/site.png" alt="Website" @click="handleClick" class="w-120" />
    </div>
</template>

<script setup lang="ts">
const handleClick = (event: MouseEvent) => {
    event.preventDefault();
    window.open("https://dev.richmoney.life", "_blank");
}
</script>