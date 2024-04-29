<template>
    <div>
        <pick-colors v-model:value="value" />
    </div>
</template>

<script lang="ts" setup>
import PickColors from 'vue-pick-colors'
const value = ref('#ff4500')
</script>