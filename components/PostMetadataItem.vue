<script setup>
const props = defineProps({
    label: String
})
</script>

<template>
    <div class="flex flex-col space-y-3">
        <b>{{ label }}</b>
        <slot />
    </div>
</template>