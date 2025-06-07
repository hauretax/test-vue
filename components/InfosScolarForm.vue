<template>
    <div @click="toggleCollapse" class="transition-all duration-1000 overflow-hidden  relative 
            flex  p-4 flex-col items-start self-stretch 
            rounded-2xl bg-white" :class="{ 'max-h-[100px]': isCollapsed, 'max-h-[2000px]': !isCollapsed }">
        <div class="flex items-center justify-between pt-2 w-full ">
            <h2 class="emphasis text-ellipsis overflow-hidden " :class="{ 'flex-1': isCollapsed, 'mb-4': !isCollapsed }"
                style="margin: 0;">
                {{ title }}
            </h2>

            <button @click="toggleCollapse" v-if="!isCollapsed" 
                class="text-black text-xl flex justify-center items-center"
                style="width: 20px; height: 20px; padding: 8px; gap: 8px;">
                ✕
            </button>
        </div>
        <div v-if="isCollapsed" class=" pb-2 text-sm italic text-gray-500 cursor-pointer">
            À compléter
        </div>

        <div v-show="!isCollapsed">
            <div v-for="(group, groupIndex) in groups" :key="groupIndex">
                <div v-if="groupIndex !== 0" class="border-t border-gray-300 my-6 px-2"></div>

                <div class="">
                    <p v-if="group.title" class="label mb-4">{{ group.title }}</p>

                    <div class="flex flex-wrap gap-2 items-start content-start self-stretch">
                        <label v-for="(item, itemIndex) in group.items" :key="itemIndex" class="cursor-pointer">
                            <input type="radio" :name="'group-' + groupIndex" :value="itemIndex"
                                v-model="selected[groupIndex]" class="hidden" />
                            <Puce :title="item.title" :active="selected[groupIndex] === itemIndex" />
                        </label>
                    </div>
                </div>
            </div>

            <div class="">
                <button @click="validateForm" :class="[
                    'button-text flex max-w-[720px] w-full px-6 py-4 mt-6 justify-center items-center text-center transition-colors',
                    isFormValid
                        ? 'rounded-full bg-black text-white'
                        : 'rounded-[1000px] bg-white text-black border border-[#646A81] opacity-50'
                ]">
                    Confirmer
                </button>
            </div>
        </div>
    </div>
</template>

<script setup>
import { reactive, ref, computed, watch } from 'vue'
import Puce from '~/components/Puce.vue'

const props = defineProps({
    title: { type: String, required: true },
    groups: { type: Array, required: true },
    isOpen: { type: Boolean, required: true }
})

const isCollapsed = ref(!props.isOpen)

watch(() => props.isOpen, (newVal) => {
    isCollapsed.value = !newVal
})

// Initialise selected avec null pour chaque groupe
const selected = reactive(Array(props.groups.length).fill(null))

function validateForm() {
    const selectionsTitles = props.groups.map((group, i) => {
        const selectedIndex = selected[i]
        return selectedIndex !== null ? group.items[selectedIndex].title : null
    })
    console.log('Form validated with selection:', selectionsTitles)
}

const isFormValid = computed(() => {
    return selected.length === props.groups.length &&
        selected.every(sel => sel !== null && sel !== '')
})

function toggleCollapse() {
    isCollapsed.value = !isCollapsed.value
}

</script>
