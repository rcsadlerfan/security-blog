<script setup>
const { data: page } = await useAsyncData('page', () => queryContent().where({ _path: { $eq: useRoute().path } }).findOne())

useHead({
    title: page.title
})
</script>

<template>
    <main class="p-5 prose prose prose-invert max-w-none">
        <ContentDoc></ContentDoc>
    </main>
</template>