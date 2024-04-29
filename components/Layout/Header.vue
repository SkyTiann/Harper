<template>
    <div class="w-full h-[4.5rem] rounded-b-lg px-4 bg-[--card-bg] flex items-center justify-between">
        <a class="h-12 hover:bg-blue-100 px-6 rounded-lg flex items-center" href="/">
            <span></span>
            <span class="text-[--primary] font-semibold">Harper</span>
        </a>
        <div class="h-12 w-80 hidden md:flex justify-between">
            <a href="/"
                class="h-full flex items-center px-2 hover:bg-blue-100 hover:text-blue-400 font-semibold rounded-lg">
                <div>Home</div>
            </a>
            <a href="/"
                class="h-full flex items-center px-2 hover:bg-blue-100 hover:text-blue-400 font-semibold rounded-lg">
                <div>Archive</div>
            </a>
            <a href="/"
                class="h-full flex items-center px-2 hover:bg-blue-100 hover:text-blue-400 font-semibold rounded-lg">
                <div>About</div>
            </a>
            <a href="/"
                class="h-full flex items-center px-2 hover:bg-blue-100 hover:text-blue-400 font-semibold rounded-lg">
                <div>Github</div>
            </a>
        </div>
        <div class="h-12 w-60 flex items-center">
            <Palette></Palette>
            <Dark></Dark>
        </div>
    </div>
</template>

<script setup lang="ts">
import Palette from '@/components/Palette/index.vue'
import Dark from '@/components/Dark/index.vue'
</script>
