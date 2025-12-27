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
              <h2></h2>
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
              <v-img src="@/assets/Holzhaustur.jpg" alt="Holz Haustüren" cover class="section-img" />
            </v-col>
            <v-col cols="12" md="5" class="section-body">
              <h3 class="section-title red">Holz Haustüren</h3>
              <p class="section-text">Natürlich und individuell. Echte Handwerksqualität mit moderner Technik und edlen Akzenten.</p>
              <v-expand-transition>
                <div v-if="expanded[0]" class="section-extra">
                  <ul class="section-list">
                    <li>Massives Holz für natürliche Ausstrahlung und Wohnlichkeit</li>
                    <li>Sehr gute Wärmedämmwerte bei richtiger Ausführung</li>
                    <li>Individuelle Gestaltung durch Fräsungen, Glas und Oberflächen</li>
                    <li>Hohe Einbruchhemmung mit moderner Beschlagtechnik</li>
                    <li>Ideal für klassische und moderne Architektur</li>
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
              <h3 class="section-title red">Holz‑Alu Haustüren</h3>
              <p class="section-text">Innen warmes Holz, außen schützendes Aluminium. Höchste Witterungsbeständigkeit und stille Eleganz.</p>
              <v-expand-transition>
                <div v-if="expanded[1]" class="section-extra">
                  <ul class="section-list">
                    <li>Witterungsbeständige Aluminium-Außenschale für lange Lebensdauer</li>
                    <li>Behagliches Holz innen für ein warmes Wohngefühl</li>
                    <li>Sehr geringer Wartungsaufwand durch robuste Oberflächen</li>
                    <li>Perfekte Kombination aus Design, Sicherheit und Komfort</li>
                    <li>Viele Farb- und Dekorvarianten außen und innen</li>
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
              <v-img src="@/assets/HolzAlutur.jpg" alt="Holz‑Alu Haustüren" cover class="section-img" />
            </v-col>
          </v-row>
        </v-container>
      </section>

      <section :class="['section section--light', { 'section--expanded': expanded[2] }]">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="6" class="section-media">
              <v-img src="@/assets/HolzSteintur.jpg" alt="Holz/Stein Haustüren" cover class="section-img" />
            </v-col>
            <v-col cols="12" md="5" class="section-body">
              <h3 class="section-title red">Holz/Stein Haustüren</h3>
              <p class="section-text">Einzigartige Kombinationen aus edlen Naturmaterialien für markante Eingangsbereiche.</p>
              <v-expand-transition>
                <div v-if="expanded[2]" class="section-extra">
                  <ul class="section-list">
                    <li>Charakterstarke Optik durch echte Stein- oder Steindekor-Oberflächen</li>
                    <li>Kombination mit Holz für ein warmes, natürliches Gesamtbild</li>
                    <li>Sehr robuste, widerstandsfähige Oberflächen</li>
                    <li>Ideal für architektonisch anspruchsvolle Eingangsbereiche</li>
                    <li>Jede Tür ein Unikat durch individuelle Materialkombination</li>
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
              <h3 class="section-title red">Aluminium Haustüren</h3>
              <p class="section-text">Robust, formstabil und energieeffizient. Große Designfreiheit dank moderner Profile.</p>
              <v-expand-transition>
                <div v-if="expanded[3]" class="section-extra">
                  <ul class="section-list">
                    <li>Sehr hohe Stabilität auch bei großen Türformaten</li>
                    <li>Beste Dauerhaftigkeit und Witterungsbeständigkeit</li>
                    <li>Optimale Wärmedämmung durch thermisch getrennte Profile</li>
                    <li>Moderne, flächenbündige Designs mit verdeckt liegenden Bändern möglich</li>
                    <li>Umfangreiche Farbpalette in RAL, Metallic und Spezialoberflächen</li>
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
              <v-img src="@/assets/Alutur.jpg" alt="Aluminium Haustüren" cover class="section-img" />
            </v-col>
          </v-row>
        </v-container>
      </section>

      <!-- Konfigurator CTA -->
      <section class="section section--light">
        <v-container class="section-container">
          <v-row>
            <v-col cols="12">
              <h3 class="section-title" style="text-align:center">Haustürkonfigurator starten / Anfrage senden</h3>
            </v-col>
            <v-col cols="12">
              <p class="configurator-desc">
                Gestalten Sie Ihre individuelle Haustür. Wählen Sie Haustürmodell, Bauform, Außenmaße, Farbe, Drücker, Zubehör und schicken Sie uns Anfrage oder Bestellung.
              </p>
              <p class="configurator-cta">
                <a href="https://configurator.varialis.net/?bpi=BC27B19A-C106-404F-96C2-60B7AC4C9FD0" target="_blank" rel="noopener" aria-label="Anfrage über den Konfigurator senden">
                  – SENDEN SIE UNS EINE ANFRAGE ÜBER DEN KONFIGURATOR –
                </a>
              </p>
            </v-col>
            <v-col cols="12">
              <a
                href="https://configurator.varialis.net/?bpi=BC27B19A-C106-404F-96C2-60B7AC4C9FD0"
                target="_blank"
                rel="noopener"
                class="configurator-link"
                aria-label="Haustürkonfigurator öffnen (neuer Tab)"
              >
                <v-img
                  src="@/assets/Hausturkonfigurator.jpg"
                  alt="Haustürkonfigurator Vorschau"
                  cover
                  class="configurator-img"
                />
              </a>
              <p class="configurator-hint">Klicken Sie auf das Bild, um den Konfigurator zu öffnen.</p>
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
import sliderTImg1 from '@/assets/TS1.png'
import sliderTImg2 from '@/assets/TS2.png'
import sliderTImg3 from '@/assets/TS3.png'



// Lokales Bild muss importiert werden, sonst findet Vite den Pfad nicht
const items = [
  sliderTImg1,
  sliderTImg2,
  sliderTImg3,
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
  /* Bildverhältnis 1080x810 ≙ 4:3 */
  width: 500px;
  max-width: 100%;
  aspect-ratio: 1080 / 810;
  height: 160px;
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
  .section-img {
    width: 70%;
    max-width: 260px;
    aspect-ratio: 1080 / 810;
    height: auto;
    object-fit: contain;
  }
  /* gleiche Hintergrundfarbe, damit keine sichtbare Kante zwischen Sections entsteht */
  .section--alt { background: #fff; }
}

@media (min-width: 1280px) {
  .hero-title { font-size: 36px; }
  .section-title { font-size: 32px; }
  .section-img { height: 420px; }
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

/* Konfigurator CTA */
.configurator-link { display: block; border: 2px solid #e5e7eb; }
.configurator-img { height: auto; max-height: 600px; background: #eee; }
.configurator-hint { text-align: center; color: #6b7280; margin-top: 8px; }
.configurator-desc { text-align: center; color: #c0392b; margin: 8px 0 0; }
.configurator-cta { text-align: center; margin: 8px 0 16px; }
.configurator-cta a { color: #c0392b; text-decoration: none; font-weight: 700; letter-spacing: 0.5px; }
</style>



