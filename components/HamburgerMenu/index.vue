<template>
    <div class="md:hidden">
        <span class="iconfont icon-hanbaobaocaidan" @click="drawerVisible = true"></span>
        <div class="fixed w-5/12 h-screen bg-[--card-bg] shadow-md top-0 right-0 translate-x-full transition-all"
            :class="{ 'translate-x-0': drawerVisible }" v-show="drawerVisible">
            <div class="iconfont icon-guanbi absolute top-2 right-2 text-lg" @click="drawerVisible = false"></div>
            <ul class="mt-10 px-3">
                <li v-for="item in Menu" class="py-3">
                    <a :href="item.route ? item.route : '/'">{{ item.title }}</a>
                </li>
            </ul>
        </div>
    </div>
</template>

<script lang="ts" setup>
import { Menu } from '@/constants/menu.constant'

const drawerVisible = ref(true)

</script>