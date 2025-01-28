<template>
    <div class="home">
      <HeaderComponent />
      <AiGuidePDF />
    </div>
  </template>
  
  <script>
  
  



import AiGuidePDF from '../components/AiGuidePDF.vue';
  import HeaderComponent from '../components/HeaderComponent.vue';
  
  export default {
    name: 'HomePage',
    components: {
      HeaderComponent,
      AiGuidePDF
    }
  }
  </script>