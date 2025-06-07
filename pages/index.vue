<template>

  <Header progress="100" />

  <div class='bg-[#F7F3F0] h-1000 p-4'>

    <SchoolCard />

    <InfosScolarForm class="my-4" title="Informations scolaires" :groups="formGroups" :isOpen="true" />

    <InfosScolarForm title="Informations scolaires 2" :groups="formGroups" :isOpen="false" />
  </div>
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