<template>
  <Navbar :logo="logoBuger" :alt="descrLogo" />
  <router-view/>
  <FooterPage />
</template>

<script>
import Navbar from '@/components/Navbar.vue';
import FooterPage from '@/components/FooterPage.vue';

export default {
  components:{
    Navbar,
    FooterPage
  },
  data(){
    return{
      logoBuger: '/img/logo.png',
      descrLogo: 'Logo da Burger e Cia'
    }
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
}
.container_main{
  text-align: center;
  min-height: 250px;
}
</style>
