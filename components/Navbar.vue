<script setup>
const links = [
    {
        label: 'Home',
        to: '/'
    },
    {
        label: 'Posts',
        to: '/posts'
    }
]
</script>

<template>
    <UHorizontalNavigation :links="links"></UHorizontalNavigation>
</template>