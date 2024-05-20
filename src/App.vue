<template>
  <Navbar />
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
  }
}
</script>

<style>

</style>
