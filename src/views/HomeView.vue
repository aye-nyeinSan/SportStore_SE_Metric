<script setup lang="ts">

  import Why from '@/components/whyShop.vue'
  import Promotion from '@/components/promotion.vue';
import Trending from '@/components/trending.vue';
import Links from '@/components/Links.vue';

import CardSlider from '@/components/cardslider.vue';
import HeroSlider from '@/components/heroSlider.vue';

import promo from '@/assets/4.png'

</script>

<template>
  <main>
    <v-container>

      <HeroSlider/>
      <div class="heading-section">
        <h1 class="heading">NEW ARRIVALS</h1>
        <p class="subheading">Get Moving, Get Grooving, Get Shopping!</p>
      </div>

      <CardSlider/>
     
    
      <div class="heading-section">
          <h1 class="heading">BEST SELLER</h1>
      </div>
      <CardSlider/>

      <Trending/>
      <Promotion/>

      <Why/>
      <Links/>

    </v-container>
  </main>
</template>
<style scoped>
.heading-section {
  text-align: center; /* Center the heading text */
  margin: 40px 0; /* Add vertical space around headings */
}

.heading {
  font-size: 36px;
  font-weight: bold;
  margin: 0;
}

.subheading {
  font-size: 18px;
  color: gray;
  margin: 10px 0;
}

</style>