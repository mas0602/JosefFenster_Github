<template>
  <v-app>
    <!-- Responsive Header (hidden on large desktop) -->
    <v-app-bar density="comfortable" flat absolute color="transparent" class="responsive-header">
      <div class="header-container">
        <img :src="logo" alt="Logo" class="header-logo" />
        <div class="spacer" />
        <!-- Only Hamburger Menu for small and laptop widths -->
        <v-menu v-model="menuOpen" location="bottom end" :close-on-content-click="true">
          <template #activator="{ props }">
            <v-btn class="nav-mobile-trigger" v-bind="props" icon="mdi-menu" color="white" aria-label="Menü" />
          </template>
          <v-list density="comfortable">
            <v-list-item v-for="(item, i) in navItems" :key="i" @click="onNav(item)">
              <v-list-item-title>{{ item.label }}</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </div>
    </v-app-bar>
    <v-main class="pa-0">
      <div class="slide">
        <v-carousel
          class="background"
          transition-duration="700"
          crossfade
          show-arrows="hover"
          hide-delimiters
          cycle
          height="70svh"
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
    
    <!-- Kacheln unter dem Slider -->
    <section class="features">
      <v-container class="features-container">
        <v-row align="stretch" justify="center" no-gutters>
          <v-col cols="12" md="3" class="feature-col">
            <v-card class="feature-card" elevation="0">
              <div class="feature-header">FENSTER</div>
              <RouterLink to="/fensterpage" class="feature-media">
                <v-img src="https://placehold.co/640x360/png?text=Fenster" cover alt="Fenster" />
              </RouterLink>
              <div class="feature-body">
                Neue Maßstäbe – Stabilität, Sicherheit und hervorragende Wärmedämmung.
              </div>
            </v-card>
          </v-col>
          <v-col cols="12" md="3" class="feature-col">
            <v-card class="feature-card" elevation="0">
              <div class="feature-header">HAUSTÜREN</div>
              <RouterLink to="/tuerenpage" class="feature-media">
                <v-img src="https://placehold.co/640x360/png?text=Haust%C3%BCren" cover alt="Haustüren" />
              </RouterLink>
              <div class="feature-body">
                Moderne oder klassische Haustüren – vielfältige Designs und Glasoptiken.
              </div>
            </v-card>
          </v-col>
          <v-col cols="12" md="3" class="feature-col">
            <v-card class="feature-card" elevation="0">
              <div class="feature-header">INNENTÜREN</div>
              <RouterLink to="/innentuerenpage" class="feature-media">
                <v-img src="https://placehold.co/640x360/png?text=Innent%C3%BCren" cover alt="Innentüren" />
              </RouterLink>
              <div class="feature-body">
                Variables Modelldesign für individuelle Gestaltungsfreiheit im Innenraum.
              </div>
            </v-card>
          </v-col>
          <v-col cols="12" md="3" class="feature-col">
            <v-card class="feature-card" elevation="0">
              <div class="feature-header">AKTIONEN</div>
              <a href="#" class="feature-media" aria-label="Aktionen ansehen">
                <v-img src="https://placehold.co/640x360/png?text=Aktionen" cover alt="Aktionen" />
              </a>
              <div class="feature-body">
                Verbinden Sie Preisvorteile mit Design, Qualität und Sicherheit.
              </div>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </section>
    
    <!-- Desktop-only Buttons (visible on large desktop only) -->
    <v-row class="btns desktop-only" align="center" justify="center" no-gutters>
      <v-btn class="menu-btn" :to="'/fensterpage'">Fenster</v-btn>
      <v-btn class="menu-btn" :to="'/tuerenpage'">Haustüren</v-btn>
      <v-btn class="menu-btn" href="https://configurator.varialis.net/?bpi=BC27B19A-C106-404F-96C2-60B7AC4C9FD0" target="_blank" rel="noopener">Haustürenkonfigurator</v-btn>
      <v-btn class="menu-btn" :to="'/innentuerenpage'">Innentüren</v-btn>
      <v-btn class="menu-btn highlight">Impressum</v-btn>
    </v-row>
  </v-app>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import logo from '@/assets/logo.png'

const items = [
  'https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg',
  'https://cdn.vuetifyjs.com/images/carousel/sky.jpg',
  'https://cdn.vuetifyjs.com/images/carousel/bird.jpg',
  'https://cdn.vuetifyjs.com/images/carousel/planet.jpg',
]

const menuOpen = ref(false)
const router = useRouter()
const navItems = [
  { label: 'Fenster' },
  { label: 'Haustüren' },
  { label: 'Haustürenkonfigurator' },
  { label: 'Innentüren' },
  { label: 'Impressum' },
]

function onNav(item) {
  menuOpen.value = false
  if (item.label === 'Fenster') {
    router.push('/fensterpage')
  } else if (item.label === 'Haustüren') {
    router.push('/tuerenpage')
  } else if (item.label === 'Haustürenkonfigurator') {
    window.open('https://configurator.varialis.net/?bpi=BC27B19A-C106-404F-96C2-60B7AC4C9FD0', '_blank', 'noopener')
  } else if (item.label === 'Innentüren') {
    router.push('/innentuerenpage')
  }
}


// no extra helpers needed; links use :to and mobile menu uses router.push
</script>

<style>
/* --- Layout --- */
.slide {
  position: relative;
  /* Use small viewport units for better mobile behavior */
  height: 100svh;
  overflow: hidden;
  isolation: isolate;
}

.background {
  width: 100% !important;
  height: 100% !important;
  z-index: 0 !important;
  position: relative;
}

/* --- Header --- */
.header-container {
  display: flex;
  align-items: center;
  width: 100%;
  padding: 0 16px;
}

.header-logo {
  height: 40px;
  width: auto;
  object-fit: contain;
}

.spacer { flex: 1; }


.nav-mobile-trigger { display: inline-flex; }

/* --- Breakpoints --- */
/* Header only for small to laptop widths; hide on large desktop */
@media (min-width: 1280px) {
  .responsive-header { display: none !important; }
}

/* Desktop button row only on large desktop */
@media (max-width: 1279.98px) {
  .desktop-only { display: none !important; }
}

/* Desktop buttons positioning (visible only when .desktop-only is shown) */
.btns.desktop-only {
  position: fixed;
  top: 24px;
  right: 24px;
  display: flex;
  flex-direction: row;
  gap: 24px;
  pointer-events: auto;
  z-index: 2147483647 !important;
}

/* --- Allgemeine Button-Stile --- */
.menu-btn {
  background: transparent !important;
  color: white !important;
  font-weight: 700 !important;
  text-transform: uppercase !important;
  font-size: 14px !important;
  box-shadow: none !important;
  transition: color 0.3s ease;
}

.menu-btn:hover {
  color: #d63031 !important;
  background: transparent;
}

/* --- Highlight-Button --- */
.highlight { color: #d63031 !important; }

/* --- Carousel Z-Index Fix --- */
.v-carousel,
.v-window,
.v-window-item,
.v-carousel .v-img,
.v-carousel .v-img__img {
  z-index: 0 !important;
}

/* --- Scrollbar unsichtbar machen --- */
::-webkit-scrollbar { width: 0px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb {
  background-color: #374151;
  border-radius: 10px;
  transition: background 0.3s;
}
::-webkit-scrollbar-thumb:hover { background-color: #d1d5db; }

/* --- Responsive adjustments --- */
@media (min-width: 480px) {
  .header-logo { height: 44px; }
  .menu-btn { font-size: 15px !important; }
}

@media (min-width: 768px) {
  .menu-btn { font-size: 16px !important; }
}

@media (min-width: 1024px) {
  .btns.desktop-only { gap: 32px; top: 28px; right: 32px; }
}

/* --- Features --- */
.features { background: #f5f5f7; padding: 32px 0; }
.features-container { max-width: 1200px; }
.feature-col { padding: 12px; }
.feature-card { background: white; border: 1px solid #e5e7eb; }
.feature-header {
  background: #e5e7eb;
  text-align: center;
  padding: 16px 12px;
  font-weight: 800;
  letter-spacing: 0.5px;
}
.feature-media { display: block; }
.feature-body { padding: 16px; color: #4b5563; text-align: center; }
</style>
