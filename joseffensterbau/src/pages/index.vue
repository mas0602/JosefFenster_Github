<template>
  <v-app>
    <header class="header">

      <v-img src="../assets/logo2.png"></v-img>




    </header>
    <div class="slide">
      <v-carousel
        class="background"
        transition-duration="700"
        crossfade
        show-arrows="hover"
        hide-delimiters
        cycle
      >
        <v-carousel-item v-for="(src, i) in items" :key="i" :src="src" cover />
      </v-carousel>
    </div>
  </v-app>
</template>

<script setup>
const items = [
  "https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg",
  "https://cdn.vuetifyjs.com/images/carousel/sky.jpg",
  "https://cdn.vuetifyjs.com/images/carousel/bird.jpg",
  "https://cdn.vuetifyjs.com/images/carousel/planet.jpg",
];
</script>

<style>
.header {
  height: 80px;
  background-color: #374151;
}

/* Wrapper: steuert Höhe + Stacking-Kontext */
.slide {
  position: relative;
  height: 80vh;
  overflow: hidden;
}

/* Carousel: füllt den Wrapper, bleibt darunter */
.background {
  position: relative; /* wichtig, damit z-index greift */
  width: 100% !important;
  height: 100% !important;
  z-index: 0;
  height: 40vh; /* unter dem Button */
}


/* Globale Scrollbar-Styling */
::-webkit-scrollbar {
  width: 0px;              /* Breite der Scrollbar */
}

::-webkit-scrollbar-track {
  background: transparent; /* Hintergrund (meist transparent oder dunkel) */
}

::-webkit-scrollbar-thumb {
  background-color: #374151; /* Scrollbalken-Farbe */
  border-radius: 10px;                        /* abgerundet */
  transition: background 0.3s;
}

::-webkit-scrollbar-thumb:hover {
  background-color: #d1d5db;
}

</style>
