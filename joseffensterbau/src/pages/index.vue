<template>
  <v-app>
    <v-main>
      <div class="slide">
        <v-carousel
          class="background"
          transition-duration="700"
          crossfade
          show-arrows="hover"
          hide-delimiters
          cycle
          height="100hv"
        >
          <v-carousel-item
            v-for="(src, i) in items"
            :key="i"
            :src="src"
            cover
          />
        </v-carousel>
      </div>
    </v-main>

    <img class="logo-fixed" :src="logo" alt="Logo" />
  <v-row class="btns">
    <v-btn class="fensterbtn">Fenster</v-btn>
    <v-btn class="türebtn">Türen</v-btn>
    <v-btn class="kontatkbtn">Kontakt</v-btn>
    <v-btn class="imressumbtn">Impressum</v-btn>
  </v-row>
  </v-app>
</template>

<script setup>
import logo from '@/assets/logo.png' // ggf. Pfad anpassen

const items = [
  'https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg',
  'https://cdn.vuetifyjs.com/images/carousel/sky.jpg',
  'https://cdn.vuetifyjs.com/images/carousel/bird.jpg',
  'https://cdn.vuetifyjs.com/images/carousel/planet.jpg',
]
</script>

<style>
/* --- Layout --- */
.slide {
  position: relative;
  height: 100vh;
  overflow: hidden;
  isolation: isolate; /* eigener Stacking-Kontext (robuster) */
}

.background {
  width: 100% !important;
  height: 100% !important;
  z-index: 0 !important; /* Carousel bewusst nach hinten */
  position: relative;
}

/* --- Logo-Overlay --- */
.logo-fixed {
  position: fixed;
  top: 16px;
  left: 16px;
  height: 80px;
  width: auto;
  object-fit: contain;
  pointer-events: none; /* blockiert keine Klicks */
  z-index: 2147483647 !important; 
}

.btns{
  position: fixed;
  width: 100px;
  pointer-events: none; /* blockiert keine Klicks */
  z-index: 2147483647 !important; 
  right: 16px;

}


.fensterbtn{
  
}

.v-carousel,
.v-window,
.v-window-item,
.v-carousel .v-img,
.v-carousel .v-img__img {
  z-index: 0 !important;
}

/* (Optional) Scrollbar-Styling */
::-webkit-scrollbar { width: 0px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb {
  background-color: #374151;
  border-radius: 10px;
  transition: background 0.3s;
}
::-webkit-scrollbar-thumb:hover { background-color: #d1d5db; }
</style>
