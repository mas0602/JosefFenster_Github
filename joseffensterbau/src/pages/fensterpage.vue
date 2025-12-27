<template>
  <v-app>
    <v-main class="pa-0">
      <!-- Compact hero slideshow -->
      <section class="hero">
        <v-carousel class="hero-carousel" hide-delimiters show-arrows="hover" cycle height="60svh" transition="fade-transition">
          <v-carousel-item
            v-for="(src, i) in items"
            :key="i"
            :src="src"
            cover
          >
            <div class="hero-overlay">
              <h2 class="hero-title"></h2>
              <p class="hero-sub"></p>
            </div>
          </v-carousel-item>
        </v-carousel>
      </section>

      <!-- Long-scroll stacked sections (Apple-style) -->
      <section :class="['section section--light', { 'section--expanded': expanded[0] }]">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="6" class="section-media">
              <v-img src="@/assets/HolzFenster_GPT.png" alt="Holz Fenster" cover class="section-img" />
            </v-col>
            <v-col cols="12" md="5" class="section-body">
              <h3 class="section-title red">Holz Fenster</h3>
              <p class="section-text">Moderne Konstruktion, langlebige Beschichtungen und natürliche Ausstrahlung. Nachhaltige Alternative für ökologisch planende Bauherren.</p>
              <v-expand-transition>
                <div v-if="expanded[0]" class="section-extra">
                  <!-- Füge hier deinen zusätzlichen Text ein -->
                  <ul class="section-list">
                    <li>Hervorragende energetische Effizienz und dauerhafte Witterungsbeständigkeit</li>
                    <li>Individuelle Optik mit natürlicher Holzmaserung</li>
                    <li>Nachhaltige Produktion aus nachwachsenden Rohstoffen</li>
                    <li>Lange Haltbarkeit bei richtiger Pflege</li>
                    <li>Vielfältige Gestaltungsmöglichkeiten</li>
                  </ul>
                </div>
              </v-expand-transition>
              <v-btn
                variant="text"
                class="section-link"
                :append-icon="expanded[0] ? 'mdi-chevron-up' : 'mdi-chevron-down'"
                @click="expanded[0] = !expanded[0]"
              >
                {{ expanded[0] ? 'Weniger' : 'Mehr' }}
              </v-btn>
            </v-col>
          </v-row>
        </v-container>
      </section>

      <section :class="['section section--alt', { 'section--expanded': expanded[1] }]">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="5" class="section-body order-md-1">
              <h3 class="section-title red">Holz-Alu Fenster</h3>
              <p class="section-text">Innen warmes Holz, außen schützendes Aluminium. Vielfältige Designs und höchste Witterungsbeständigkeit.</p>
              <v-expand-transition>
                <div v-if="expanded[1]" class="section-extra">
                  <!-- Füge hier deinen zusätzlichen Text ein -->
                  <ul class="section-list">
                    <li>Dauerhaftes Aluminium für moderne Optik außen</li>
                    <li>Warmes Holz für Wohnlichkeit innen</li>
                    <li>Höchste Witterungsbeständigkeit</li>
                    <li>Minimaler Wartungsaufwand</li>
                    <li>Premium Design und Langlebigkeit</li>
                  </ul>
                </div>
              </v-expand-transition>
              <v-btn
                variant="text"
                class="section-link"
                :append-icon="expanded[1] ? 'mdi-chevron-up' : 'mdi-chevron-down'"
                @click="expanded[1] = !expanded[1]"
              >
                {{ expanded[1] ? 'Weniger' : 'Mehr' }}
              </v-btn>
            </v-col>
            <v-col cols="12" md="6" class="section-media order-md-2">
              <v-img src="@/assets/HolzAluFenster_GPT.png" alt="Holz-Alu Fenster" cover class="section-img" />
            </v-col>
          </v-row>
        </v-container>
      </section>

      <section :class="['section section--light', { 'section--expanded': expanded[2] }]">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="6" class="section-media">
              <v-img src="@/assets/AluFenster_GPT.png" alt="Aluminium Fenster" cover class="section-img" />
            </v-col>
            <v-col cols="12" md="5" class="section-body">
              <h3 class="section-title red">Aluminium Fenster</h3>
              <p class="section-text">Stabilität, Langlebigkeit und schlanke Profile. Hervorragende Wärmedämmung dank thermischer Trennung.</p>
              <v-expand-transition>
                <div v-if="expanded[2]" class="section-extra">
                  <!-- Füge hier deinen zusätzlichen Text ein -->
                  <ul class="section-list">
                    <li>Design trifft Qualität - moderne Ästhetik</li>
                    <li>Thermisch getrennte Profilsysteme für höchste Wärmedämmung</li>
                    <li>Schmale Profilansichten für maximale Glasflächen</li>
                    <li>Korrosionsbeständig und wartungsarm</li>
                    <li>Große Gestaltungsfreiheit in Farbe und Form</li>
                  </ul>
                </div>
              </v-expand-transition>
              <v-btn
                variant="text"
                class="section-link"
                :append-icon="expanded[2] ? 'mdi-chevron-up' : 'mdi-chevron-down'"
                @click="expanded[2] = !expanded[2]"
              >
                {{ expanded[2] ? 'Weniger' : 'Mehr' }}
              </v-btn>
            </v-col>
          </v-row>
        </v-container>
      </section>

      <section :class="['section section--alt', { 'section--expanded': expanded[3] }]">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="5" class="section-body order-md-1">
              <h3 class="section-title red">Kunststoff Fenster</h3>
              <p class="section-text">Vielseitige Profilsysteme für alle Anforderungen: Qualität, Design, Funktionalität und Umweltfreundlichkeit.</p>
              <v-expand-transition>
                <div v-if="expanded[3]" class="section-extra">
                  <!-- Füge hier deinen zusätzlichen Text ein -->
                  <ul class="section-list">
                    <li>Hervorragendes Preis-Leistungs-Verhältnis</li>
                    <li>Ausgezeichnete Wärmedämmung</li>
                    <li>Minimaler Pflegeaufwand</li>
                    <li>Langlebig und umweltfreundlich</li>
                    <li>Vielfältige Farb- und Designoptionen</li>
                  </ul>
                </div>
              </v-expand-transition>
              <v-btn
                variant="text"
                class="section-link"
                :append-icon="expanded[3] ? 'mdi-chevron-up' : 'mdi-chevron-down'"
                @click="expanded[3] = !expanded[3]"
              >
                {{ expanded[3] ? 'Weniger' : 'Mehr' }}
              </v-btn>
            </v-col>
            <v-col cols="12" md="6" class="section-media order-md-2">
              <v-img src="@/assets/KunststoffFenster_GPT.png" alt="Kunststoff Fenster" cover class="section-img" />
            </v-col>
          </v-row>
        </v-container>
      </section>
    </v-main>

    <!-- Footer -->
    <SiteFooter />
  </v-app>

  <!-- Desktop-only Buttons (visible on large desktop only) -->
  <v-row v-if="showButtons" class="btns desktop-only" align="center" justify="center" no-gutters>
    <v-btn class="menu-btn" :to="'/'">Startseite</v-btn>
    <v-btn class="menu-btn" :to="'/fensterpage'">Fenster</v-btn>
    <v-btn class="menu-btn" :to="'/tuerenpage'">Haustüren</v-btn>
    <v-btn class="menu-btn" href="https://configurator.varialis.net/?bpi=BC27B19A-C106-404F-96C2-60B7AC4C9FD0" target="_blank" rel="noopener">Haustürenkonfigurator</v-btn>
    <v-btn class="menu-btn" :to="'/innentuerenpage'">Innentüren</v-btn>
      <v-btn class="menu-btn highlight" :to="'/impressum'">Impressum</v-btn>
  </v-row>
  
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import SiteFooter from '@/components/SiteFooter.vue'
import sliderFImg1 from '@/assets/FENSTER-SLIDER1.png'
import sliderFImg2 from '@/assets/FENSTER-SLIDER2.png'
import sliderFImg3 from '@/assets/FENSTER-SLIDER3.png'



// Lokales Bild muss importiert werden, sonst findet Vite den Pfad nicht
const items = [
  sliderFImg1,
  sliderFImg2,
  sliderFImg3,
]

// Expand/Collapse state per section
const expanded = ref([false, false, false, false])
const showButtons = ref(true)

function handleScroll() {
  showButtons.value = window.scrollY < 80
}

onMounted(() => {
  handleScroll()
  window.addEventListener('scroll', handleScroll, { passive: true })
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
/* Hero */
.hero { background: #000; }
.hero-carousel { position: relative; }
.hero-img { opacity: 0.6; }
.hero-overlay {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  color: white;
  padding: 24px;
}
.hero-title { font-size: 28px; font-weight: 800; margin: 0 0 8px; }
.hero-sub { opacity: 0.9; }

/* Sections */
.section {
  padding: 56px 0;
  transition: padding 180ms ease;
}
.section--light { background: #fff; }
.section--alt { background: #f5f5f7; }
.section-container { max-width: 1200px; }
.section-media { order: 1; }
.section-body { order: 2; }
.section-img {
  width: 250px;
  max-width: 100%;
  height: auto;
  background: transparent;
  object-fit: contain;
  display: block;
  margin: 0 auto;
  border-radius: 12px;
  overflow: hidden;
}
.section-title { font-size: 28px; font-weight: 800; margin: 0 0 12px; text-transform: uppercase; }
.section-title.red { color: #d63031; }
.section-text { color: #4b5563; margin: 0 0 12px; }
.section-link { color: #6b7280 !important; text-transform: none !important; }
.section-extra {
  margin-top: 12px;
  color: #4b5563;
  line-height: 1.6;
  transition: opacity 160ms ease;
}
.section-list {
  margin: 8px 0 0;
  padding-left: 20px;
  display: grid;
  gap: 6px;
}
.section--expanded { padding: 72px 0; }

/* Ordering helpers for alternating layout */
@media (min-width: 960px) {
  .order-md-1 { order: 1; }
  .order-md-2 { order: 2; }
  .section-media { order: initial; }
  .section-body { order: initial; }
}

/* Responsive tweaks */
@media (max-width: 959.98px) {
  .hero-title { font-size: 22px; }
  .section { padding: 40px 0; }
  /* höheres Bild auf mobilen Geräten */
  .section-img {
    width: auto;
    height: 160px;
    max-width: none;
    height: 448px;
    object-fit: cover;
  }
  /* gleiche Hintergrundfarbe, damit keine sichtbare Kante zwischen Sections entsteht */
  .section--alt { background: #fff; }
}

@media (min-width: 1280px) {
  .hero-title { font-size: 36px; }
  .section-title { font-size: 32px; }
}

/* Desktop-only buttons like on homepage */
@media (max-width: 1279.98px) {
  .desktop-only { display: none !important; }
}
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
.menu-btn {
  background: transparent !important;
  color: white !important;
  font-weight: 700 !important;
  text-transform: uppercase !important;
  font-size: 14px !important;
  box-shadow: none !important;
  transition: color 0.3s ease;
}
.menu-btn:hover { color: #d63031 !important; background: transparent; }
.highlight { color: #d63031 !important; }
</style>


