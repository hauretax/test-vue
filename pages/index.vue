<template>

  <Header progress="100" />

  <div class='h-screen bg-[#F7F3F0] p-4 '>
    <div class=' max-w-[720px] mx-auto'>
      <SchoolCard />

      <InfosScolarForm class="my-4" title="En quelle classe es-tu ?" :groups="formGroups" :isOpen="true" />
      <InfosScolarForm class="my-4" title="Spécialités" :groups="formGroups" :isOpen="false" />
      <InfosScolarForm class="my-4" title="Notes" :groups="formGroups" :isOpen="false" />
      <InfosScolarForm class="my-4" title="Résultats au bac" :groups="formGroups" :isOpen="false" />
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
      { title: 'Seconde' },
      { title: 'Première' },
      { title: 'Terminale' }
    ]
  },
  {
    title: 'Filière',
    items: [
      { title: 'Général' },
      { title: 'Technologique' },
      { title: 'Professionnel' }
    ]
  }
]
</script>