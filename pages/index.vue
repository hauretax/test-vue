<template>

  <Header progress="100" />

  <div class=' bg-[#F7F3F0] h-1000 p-4 '>
    <div class=' max-w-[720px] mx-auto'>
      <SchoolCard />

      <InfosScolarForm class="my-4" title="Informations scolaires" :groups="formGroups" :isOpen="true" />

      <InfosScolarForm title="Informations scolaires 2" :groups="formGroups" :isOpen="false" />
    </div>
  </div>

  <NuxtLink to="/application"
    class="fixed bottom-4 right-4 bg-purple-700 text-white px-4 py-2 rounded shadow-lg hover:bg-purple-800 transition">
    Application
  </NuxtLink>

</template>

<script setup>


const formGroups = [
  {
    title: null,
    items: [
      { title: 'Collège' },
      { title: 'Lycée' },
      { title: 'Université' }
    ]
  },
  {
    title: 'Filière',
    items: [
      { title: 'Scientifique' },
      { title: 'Littéraire' },
      { title: 'Économique' }
    ]
  }
]
</script>