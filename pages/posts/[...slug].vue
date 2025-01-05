<script setup>
const { data: page } = await useAsyncData('page', () => queryContent().where({ _path: { $eq: useRoute().path } }).findOne())

useHead({
    title: page.title
})
</script>

<template>
    <div class="flex items-stretch space-x-5 divide divide-x divide-gray-500">
        <main class="
            grow
            p-5 
            prose 
            prose-invert 
            max-w-none
            prose-img:m-auto
            prose-img:block
            prose-img:w-96
            prose-img:my-16"
        >
            <ContentDoc></ContentDoc>
        </main>
        <div class="px-5 w-80 shrink-0 space-y-5">
            <PostMetadataItem label="Tags">
                <div class="space-x-3">
                    <UBadge v-for="t in page.tags" :key="t">{{ t }}</UBadge>
                </div>
            </PostMetadataItem>
        </div>
    </div>
</template>