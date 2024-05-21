<template>
  <Banner />
  <div class="container_main">
    <h1>Monte o seu Burger</h1>
    <BurgerForms />
  </div>
</template>

<script>
import Banner from '@/components/Banner.vue';
import BurgerForms from '@/components/BurgerForms.vue';

export default {
  name: 'HomeView',
  components: {
    Banner,
    BurgerForms,
  }
}
</script>
