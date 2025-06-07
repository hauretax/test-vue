<template>
    <header class="flex flex-col p-4 border-b-[2px] border-b-black/10 bg-[#F7F3F0]" style="gap: 12px;">
        <div class="flex flex-1 items-center gap-3" style="flex: 1 0 0;">
            <div class="flex justify-center items-center" style="width: 146px; height: 28px;">
                <img src="/Mode_Isolation.svg" alt="Logo" class="max-w-full max-h-full" />
            </div>

        </div>
    </header>
    <div class="bg-[#1B1B1B]" style="width: 250px; height: 4px;">
        <div class="bg-[#F7F3F0]"
            :style="{ width: progress + '%', height: '4px', backgroundColor: '#1B1B1B' }"></div>
    </div>
</template>

<script setup>
defineProps({
    progress: {
        type: Number,
        default: 0,
        validator: (v) => v >= 0 && v <= 100,
    },
});
</script>
