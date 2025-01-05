<script setup>
const links = [
    {
        label: 'Home',
        to: '/'
    },
    {
        label: 'Posts',
        to: '/posts'
    },
    {
        label: 'About',
        to: '/about'
    }
]
</script>

<template>
    <UHorizontalNavigation :links="links"></UHorizontalNavigation>
</template>