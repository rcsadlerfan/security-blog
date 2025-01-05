<script setup>
const { data: posts } = await useAsyncData('home', () => 
    queryContent('posts')
        .where({
            tags: {
                $contains: 'featured'
            }
        })
        .find()
)
</script>

<template>
    <div class="p-5 space-y-5">
        <h1 class="text-3xl">Featured Posts</h1>
        <div class="grid grid-cols-4 gap-5">
            <PostCard
                v-for="p in posts"
                :key="p._path"
                :post="p"
            >
            </PostCard>
        </div>
    </div>
</template>