<template>
    <div class="inline-flex items-start py-2 px-4 rounded-[24px] transition-colors duration-300"
        :class="active ? 'border' : ''" :style="{
            borderColor: active ? 'var(--Black, #1B1B1B)' : 'transparent',
            backgroundColor: active ? 'var(--White, #FFF)' : 'var(--Beige, #F7F3F0)'
        }">
        <span class="text-base">
            {{ title }}
        </span>
    </div>
</template>

<script setup>
defineProps({
    active: {
        type: Boolean,
        default: false
    },
    title: {
        type: String,
        required: true
    }
})
</script>
