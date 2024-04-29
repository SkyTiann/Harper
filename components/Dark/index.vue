<template>
    <div class="h-10 w-20 relative cursor-pointer rounded-md flex items-center">
        <div class="hover:bg-blue-100" @click="unfold = !unfold">
            <span class="iconfont icon-taiyang text-xl"></span>
            <span>Theme</span>
        </div>
        <ul class="absolute top-10 shadow-lg drop-shadow-lg bg-[--card-bg] w-40 rounded-md px-2 py-2" v-show="unfold">
            <li class="py-1 hover:bg-blue-100 rounded-md px-2" @click="changeTheme(Theme.OsDefault)">
                <span class="iconfont icon-gensuixitong-hei text-base mr-2 text-slate-500"></span>
                <span class="text-sm">OS Default</span>
            </li>
            <li class="py-1 hover:bg-blue-100 rounded-md px-2" @click="changeTheme(Theme.Light)">
                <span class="iconfont icon-taiyang text-lg mr-2"></span>
                <span class="text-sm">Light</span>
            </li>
            <li class="py-1 hover:bg-blue-100 rounded-md px-2" @click="changeTheme(Theme.Dark)">
                <span class="iconfont icon-yueliang text-lg mr-2"></span>
                <span class="text-sm">Dark</span>
            </li>
        </ul>
    </div>
</template>

<script lang="ts" setup>
import { LocalStorageKeys, Theme } from '@/constants/key.constant'
const unfold = ref(false)


const changeTheme = (theme: Theme) => {
    window.localStorage.setItem(LocalStorageKeys.Theme, theme)
}

onMounted(() => {
    const historyMode = window.localStorage.getItem(LocalStorageKeys.Theme) as (Theme | null)
    let mode = historyMode
    if (historyMode === null) {
        window.localStorage.setItem(LocalStorageKeys.Theme, Theme.OsDefault)
        mode = Theme.OsDefault
    }
    console.log(mode)
    /** 根据 mode 设置主题 */
    const setTheme = () => { 

    }


    // const mqList = window.matchMedia('(prefers-color-scheme: dark)')
    // mqList.addEventListener('change', (event) => {
    //     const mode = event.matches ? 'dark' : 'light'
    //     const html = document.documentElement
    //     html.setAttribute('mode', mode)
    // })
})
</script>