<template>
        <div class="flex flex-col justify-center items-center position-relative p-5 pt-20">
            <p class="text-2xl font-bold z-10 bg-gradient-to-r from-red-500 via-white to-blue-500 bg-clip-text text-transparent">Founding Fathers</p>
            <img src="../assets/america.png" alt="America" class="w-full rounded-md h-full object-cover position-absolute top-0 left-0 -z-0 opacity-20" />
            <div class="flex flex-row justify-evenly items-center gap-4 position-relative p-5 z-10">
                <PersonFrame img="./assets/people/breneis.png" name="Leo Breneis" role="Fullstack + Founding Father" />
                <PersonFrame img="./assets/people/klein.png" name="Eros Klein" role="Fullstack + Founding Father" />
            </div>
        </div>
</template>

<script setup lang="ts">
</script>