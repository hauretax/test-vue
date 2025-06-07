<template>
  <div class='bg-black h-1000' >
    <h1>Training</h1>
    <Puce :active="true" title="Active item" />
    <Puce :active="false" title="non Active item" />


    <InfosScolarForm class="my-4" title="Informations scolaires" :groups="formGroups":isOpen="true" />
    
    <InfosScolarForm title="Informations scolaires 2" :groups="formGroups":isOpen="false" />
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