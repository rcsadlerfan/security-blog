<script setup>
const props = defineProps({
    post: Object
})
</script>

<template>
    <UCard>
        <div class="space-y-5">
            <div class="flex justify-between items-center">
                <ULink :to="post._path" class="text-xl underline text-primary">{{ post.title }}</ULink>
                <UIcon v-if="post.tags.includes('featured')" name="i-heroicons-star-solid" class="text-primary w-6 h-6"></UIcon>
            </div>
            <p>{{ post.description }}</p>
        </div>
        <template #footer>
            <div class="space-x-3">
                <UBadge
                    v-for="t in post.tags"
                    :key="t"
                >
                    {{ t }}
                </UBadge>
            </div>
        </template>
    </UCard>
</template>