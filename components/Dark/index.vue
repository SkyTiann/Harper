<template>
    <div class="h-10 w-32 relative cursor-pointer rounded-md flex items-center" @click.stop="() => { }">
        <div @click="themeClick">
            <span class="iconfont text-xl mr-1" :class="[icon]"></span>
            <span>Theme</span>
        </div>
        <ul class="absolute top-10 shadow-lg drop-shadow-lg bg-[--card-bg] w-40 rounded-md px-2 py-2" v-show="unfold">
            <li class="py-1 rounded-md px-2" :class="{ 'bg-[--list-item-bg-active]': currentTheme === Theme.OsDefault }"
                @click="changeTheme(Theme.OsDefault)">
                <span class="iconfont icon-gensuixitong-hei text-base mr-2"></span>
                <span class="text-sm">OS Default</span>
            </li>
            <li class="py-1 rounded-md px-2" :class="{ 'bg-[--list-item-bg-active]': currentTheme === Theme.Light }"
                @click="changeTheme(Theme.Light)">
                <span class="iconfont icon-taiyang text-lg mr-2"></span>
                <span class="text-sm">Light</span>
            </li>
            <li class="py-1 rounded-md px-2" :class="{ 'bg-[--list-item-bg-active]': currentTheme === Theme.Dark }"
                @click="changeTheme(Theme.Dark)">
                <span class="iconfont icon-yueliang text-lg mr-2"></span>
                <span class="text-sm">Dark</span>
            </li>
        </ul>
    </div>
</template>

<script lang="ts" setup>
import { LocalStorageKeys, Theme } from '@/constants/key.constant'
const unfold = ref(false)
const currentTheme = ref('')
const icon = computed(() => {
    const mappingTables = {
        [Theme.OsDefault]: 'icon-gensuixitong-hei',
        [Theme.Light]: 'icon-taiyang',
        [Theme.Dark]: 'icon-yueliang'
    }
    return mappingTables[currentTheme.value as Theme]
})

const setTheme = (theme: Theme) => {
    const strategy = {
        [Theme.OsDefault]: () => {
            const mqList = window.matchMedia('(prefers-color-scheme: dark)')
            const themeAutoHandler = () => {
                const historyMode = window.localStorage.getItem(LocalStorageKeys.Theme) as Theme
                if (historyMode !== Theme.OsDefault) return
                const mode = mqList.matches ? Theme.Dark : Theme.Light
                document.documentElement.setAttribute('mode', mode)
            }
            themeAutoHandler()
            /** 多次对同一个元素使用addEventListener添加同一个监听器函数，那么这个监听器函数只会被添加一次。 */
            mqList.addEventListener('change', themeAutoHandler)
        },
        [Theme.Light]: () => {
            document.documentElement.setAttribute('mode', Theme.Light)
        },
        [Theme.Dark]: () => {
            document.documentElement.setAttribute('mode', Theme.Dark)
        }
    }
    currentTheme.value = theme
    strategy[theme]()
}

const changeTheme = (theme: Theme) => {
    window.localStorage.setItem(LocalStorageKeys.Theme, theme)
    setTheme(theme)
}

const closeThemeList = () => {
    unfold.value = false
}

const themeClick = () => {
    unfold.value = !unfold.value
    document.body.removeEventListener('click', closeThemeList)
    if (unfold.value)
        document.body.addEventListener('click', closeThemeList, { once: true })
}

onMounted(() => {
    const setDefaultThemeStorageKey = () => {
        const historyMode = window.localStorage.getItem(LocalStorageKeys.Theme) as (Theme | null)
        if (historyMode === null) {
            window.localStorage.setItem(LocalStorageKeys.Theme, Theme.OsDefault)
        }
    }
    setDefaultThemeStorageKey()
    const theme = window.localStorage.getItem(LocalStorageKeys.Theme) as Theme
    currentTheme.value = theme
    setTheme(theme)
})
</script>