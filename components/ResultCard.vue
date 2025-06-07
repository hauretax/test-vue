<template>
    <div class="max-w-md mx-auto p-4 border rounded shadow">
        <div class="flex justify-between items-center mb-2">
            <div class="text-sm text-gray-500 font-medium">{{ subTitle }}</div>
            <button @click="$emit('close')" aria-label="Close"
                class="text-gray-400 hover:text-gray-700 font-bold text-xl leading-none">
                &times;
            </button>
        </div>

        <h2 class="text-xl font-semibold mb-4">{{ title }}</h2>

        <div class="flex justify-between items-center mb-4">
            <div class="text-gray-700 font-medium">Mes chances</div>
            <span :class="['px-3 py-1 rounded-full font-semibold text-sm', couleurEtiquette]">
                {{ etiquette }}
            </span>
        </div>

        <button @click="voirPlusVisible = !voirPlusVisible" class="text-blue-600 hover:underline mb-4">
            {{ voirPlusVisible ? "Voir moins" : "Voir plus" }}
        </button>

        <div v-if="voirPlusVisible" class="mb-4 text-gray-700 text-sm">
            Tu n'as pas renseigné ton lycée d'origine, or cette information rentre dans l'estimation des chances
            d'admission, surtout pour les formations les plus sélectives. Nous réduisons en conséquence notre indice de
            confiance. Tu peux toujours le renseigner !
        </div>

        <div class="flex items-center space-x-1">
            <template v-for="n in 5" :key="n">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6"
                    :class="n <= valeur ? 'text-yellow-400' : 'text-gray-300'" fill="currentColor" viewBox="0 0 20 20"
                    aria-hidden="true">
                    <path
                        d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.286 3.966a1 1 0 00.95.69h4.18c.969 0 1.371 1.24.588 1.81l-3.385 2.455a1 1 0 00-.364 1.118l1.287 3.966c.3.921-.755 1.688-1.54 1.118L10 13.347l-3.385 2.455c-.784.57-1.838-.197-1.539-1.118l1.287-3.966a1 1 0 00-.364-1.118L3.615 9.393c-.783-.57-.38-1.81.588-1.81h4.18a1 1 0 00.95-.69l1.286-3.966z" />
                </svg>
            </template>
            <span class="ml-2 text-gray-600 text-sm">Indice de confiance</span>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from "vue";

const props = defineProps({
    title: {
        type: String,
        required: true,
    },
    subTitle: {
        type: String,
        required: true,
    },
    valeur: {
        type: Number,
        required: true,
        validator: (v) => v >= 1 && v <= 5,
    },
});

const voirPlusVisible = ref(false);
let etiquette = "";
let couleurEtiquette = "";
switch (true) {
    case props.valeur <= 1:
        etiquette = "Faibles";
        couleurEtiquette = "bg-[#FAAD141A] text-[#5C3900]";
        break;
    case props.valeur <= 2:
        etiquette = "Moyenne";
        couleurEtiquette = "bg-red-200 text-red-800";
        break;
    case props.valeur === 3:
        etiquette = "élevée";
        couleurEtiquette = "bg-yellow-200 text-yellow-800";
        break;
    case props.valeur >= 4:
        etiquette = "Très élevée";
        couleurEtiquette = "bg-green-200 text-green-800";
        break;
}
</script>

<style scoped>
button {
    outline: none;
}
</style>
