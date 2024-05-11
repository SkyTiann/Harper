<template>
    <div class="w-full h-[4.5rem] rounded-b-lg px-4 bg-[--card-bg] flex items-center justify-between">
        <a class="h-12 hover:bg-blue-100 px-6 rounded-lg flex items-center" href="/">
            <span></span>
            <span class="text-[--primary] font-semibold">Harper</span>
        </a>
        <div class="h-12 w-80 hidden md:flex justify-between">
            <a v-for="item in Menu" :key="item.title" :href="item.route ? item.route : '/'"
                class="h-full flex items-center px-2 hover:bg-[--list-item-bg-hover] hover:text-[--primary] font-semibold rounded-lg">
                <div>{{ item.title }}</div>
            </a>
        </div>
        <div class="h-12 flex items-center gap-5 mr-10">
            <Dark></Dark>
            <HamburgerMenu></HamburgerMenu>
        </div>
    </div>
</template>

<script setup lang="ts">
import Dark from '@/components/Dark/index.vue'
import HamburgerMenu from '@/components/HamburgerMenu/index.vue'
import { Menu } from '@/constants/menu.constant'
</script>
