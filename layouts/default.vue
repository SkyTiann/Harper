<template>
    <div class="min-h-screen bg-[--page-bg]">
        <div class="flex flex-col min-h-screen max-w-7xl mx-auto">
            <Header class="mb-4"></Header>
            <div class="lg:flex flex-row-reverse gap-4 mb-8">
                <div class="bg-[--card-bg] w-full h-96 mb-4">
                </div>
                <div class="lg:w-72 w-full shrink-0">
                    <PersonalInfo class="mb-4"></PersonalInfo>
                    <Categories class="mb-4"></Categories>
                    <Tags></Tags>
                </div>
            </div>
            <Footer class="mt-auto"></Footer>
        </div>
    </div>
</template>

<script setup lang="ts">
import Header from '@/components/Layout/Header.vue';
import PersonalInfo from '@/components/Layout/PersonalInfo.vue';
import Categories from '@/components/Layout/Categories.vue';
import Tags from '@/components/Layout/Tags.vue';
import Footer from '@/components/Layout/Footer.vue'
</script>
