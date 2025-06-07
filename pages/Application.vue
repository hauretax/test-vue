<template>
  <Header progress="100" />
  <NuxtLink to="/" class="button-text flex px-6 py-4 mt-6 text-center rounded-full ">
    Modifier mon profil
  </NuxtLink>
  <ResultCard title="'test title'" :subTitle="'test subtitle'" :valeur="1" />

  <button
    class="button-text w-[234px] px-6 py-4 mt-6 justify-center items-center text-center rounded-full bg-black text-white mx-auto ">
    Confirmer
  </button>
</template>

<script setup>
</script>