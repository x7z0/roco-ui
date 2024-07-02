<script setup>
import { RouterLink, RouterView } from 'vue-router'


import PageHeader from './components/PageHeader.vue'
import logo from '@/assets/logo.png'
console.log(logo)

</script>

<template>

  <header id="header">
    
    <PageHeader :icon-url='logo' siteName="">1</PageHeader>
  </header>
  <main>
    <div class="content">
        <RouterView />
    </div>
    
  </main>
  



</template>

<style scoped>

.content{
  height: auto;
  overflow: auto;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}







nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  mai {
    display: grid;
    grid-template-columns: 1fr 2fr;
    
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

 

  
}
</style>
