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
              <v-img src="@/assets/InnenUrban.png" alt="Innentüren URBAN" cover class="section-img" />
            </v-col>
            <v-col cols="12" md="5" class="section-body">
              <h3 class="section-title red">Innentüren URBAN</h3>
              <p class="section-text">Schlichte klare Formen, dekorative Kontraste und individuelle Holz-Lack-Kombinationen bestimmen das Erscheinungsbild dieser Türen-Serie. Darüber hinaus zeichnen sich die primär reinweißen Türen durch ihre Unabhängigkeit von der Einrichtung aus.</p>
              <v-expand-transition>
                <div v-if="expanded[0]" class="section-extra">
                  <ul class="section-list">
                    <li>Die teilweise bündige Konstruktion und die deckend glatte Ausführung passen sich harmonisch in die vorhandene Architektur ein</li>
                    <li>Durch die ausgezeichneten Türkonstruktionen sind auch raumhohe Lösungen machbar</li>
                    <li>Die neuen flächenbündigen Drücker passen sehr gut zum schlichten Design</li>
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
              <h3 class="section-title red">Innentüren NATURA</h3>
              <p class="section-text">Die haptische Wahrnehmung, das Erfühlen der Hautsinne, von Strukturen, die Wärme der Oberfläche, ist mit unserer neuen Natura Serie in eine andere Ebene gedrungen.</p>
              <v-expand-transition>
                <div v-if="expanded[1]" class="section-extra">
                  <ul class="section-list">
                    <li>Das Naturprodukt Holz wird mit einer rein natürlichen Öloberfläche veredelt. Das Öl besteht aus Leinöl, Sonnenblumenöl, Sojaöl, Karnaubawachs (aus der brasilianischen Fächerpflanze) und Bienenwachs</li>
                    <li>Die Oberfläche lebt mit. Eine schöne natürliche Farbveränderung entsteht im Lauf der Zeit</li>
                    <li>Kratzer sind leicht ausbesserbar</li>
                    <li>Durch die offenen Poren erfolgt ein Feuchtigkeitsaustausch, der mithilft das Raumklima zu regulieren</li>
                    <li>Schmutz ist leicht abwischbar. Das Öl erfordert aber auch Pflege. Einmal jährlich sollten die Türen aufgefrischt werden</li>
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
              <v-img src="@/assets/InnenNatura.png" alt="Innentüren NATURA" cover class="section-img" />
            </v-col>
          </v-row>
        </v-container>
      </section>

      <section :class="['section section--light', { 'section--expanded': expanded[2] }]">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="6" class="section-media">
              <v-img src="@/assets/InnenLife.png" alt="Innentüren LIFE" cover class="section-img" />
            </v-col>
            <v-col cols="12" md="5" class="section-body">
              <h3 class="section-title red">Innentüren LIFE</h3>
              <p class="section-text">Ein Baum mit Tradition, eine robuste Holzart mit einer langen Geschichte. Eiche liegt wieder voll im Trend. Hinzukommt Nuss, ein sehr edles und hochwertiges Holz.</p>
              <v-expand-transition>
                <div v-if="expanded[2]" class="section-extra">
                  <ul class="section-list">
                    <li>Die bündige Konstruktion und die variablen Oberflächen-Optiken rücken diese Türen-Serie für die unterschiedlichsten Wohnsituationen ins rechte Licht</li>
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
              <h3 class="section-title red">Innentüren HOME</h3>
              <p class="section-text">Das am meisten genutzte Holz in der Türenserie Home ist der kanadische Nationalbaum: die Maple (auf Deutsch Ahorn). Sie passt durch Ihre wunderschöne Farbe und Ihre Härte ausgezeichnet in die Serie.</p>
              <v-expand-transition>
                <div v-if="expanded[3]" class="section-extra">
                  <ul class="section-list">
                    <li>Formen und Farben sind so gewählt, dass sie sehr gut miteinander harmonieren und man sich lange an ihnen erfreuen kann</li>
                    <li>Um die Individualität herauszuheben sind in dieser Serie Holzarten miteinander kombinierbar</li>
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
              <v-img src="@/assets/InnenHome.png" alt="Innentüren HOME" cover class="section-img" />
            </v-col>
          </v-row>
        </v-container>
      </section>


      <section :class="['section section--light', { 'section--expanded': expanded[4] }]">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="6" class="section-media">
              <v-img src="@/assets/InnenKlassik.png" alt="Innentüren KLASSIK" cover class="section-img" />
            </v-col>
            <v-col cols="12" md="5" class="section-body">
              <h3 class="section-title red">Innentüren KLASSIK</h3>
              <p class="section-text">Diese Türenserie wurde eigens entwickelt, um edle Villen und Stadtwohnungen authentisch ausstatten zu können.</p>
              <v-expand-transition>
                <div v-if="expanded[4]" class="section-extra">
                  <ul class="section-list">
                    <li>Durch echte Handwerkskunst und gewissenhafte Ausführung, gepaart mit hochwertigen Materialien und brillanten Oberflächen entstehen Türen in beeindruckender Optik und präziser Funktionsweise</li>
                  </ul>
                </div>
              </v-expand-transition>
              <v-btn
                variant="text"
                class="section-link"
                :append-icon="expanded[4] ? 'mdi-chevron-up' : 'mdi-chevron-down'"
                @click="expanded[4] = !expanded[4]"
              >
                {{ expanded[4] ? 'Weniger' : 'Mehr' }}
              </v-btn>
            </v-col>
          </v-row>
        </v-container>
      </section>

      <section :class="['section section--alt', { 'section--expanded': expanded[5] }]">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="5" class="section-body order-md-1">
              <h3 class="section-title red">Innentüren RUSTIKAL</h3>
              <p class="section-text">Bodenständig, bewährt, klassisch - das ist der Weg auf dem wir Tiroler Handwerks- und Designkunst zu einem harmonischen Ganzen verschmelzen lassen.</p>
              <v-expand-transition>
                <div v-if="expanded[5]" class="section-extra">
                  <ul class="section-list">
                    <li>Die Baureihe RUSTIKAL sind echte gestemmte Füllungstüren in bester Qualität und Holzverarbeitung, deren Türblätter als Rahmentüren mit Schlitz und Zapfen Verbindungen mit echten abgeplatteten Füllungen gefertigt werden</li>
                    <li>Auch Friesfurnierte Türen wie das Modell Sterzing kommen zum Einsatz, damit auch für die Gastronomie alle notwendigen Funktionen wie Feuerschutz und Schallschutz erfüllt werden können</li>
                  </ul>
                </div>
              </v-expand-transition>
              <v-btn
                variant="text"
                class="section-link"
                :append-icon="expanded[5] ? 'mdi-chevron-up' : 'mdi-chevron-down'"
                @click="expanded[5] = !expanded[5]"
              >
                {{ expanded[5] ? 'Weniger' : 'Mehr' }}
              </v-btn>
            </v-col>
            <v-col cols="12" md="6" class="section-media order-md-2">
              <v-img src="@/assets/InnenRustikal.png" alt="Innentüren RUSTIKAL" cover class="section-img" />
            </v-col>
          </v-row>
        </v-container>
      </section>

      <section :class="['section section--light', { 'section--expanded': expanded[6] }]">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="6" class="section-media">
              <v-img src="@/assets/InnenGanzglas.png" alt="Innentüren GANZGLAS" cover class="section-img" />
            </v-col>
            <v-col cols="12" md="5" class="section-body">
              <h3 class="section-title red">INNENTÜREN GANZGLAS</h3>
              <p class="section-text">Glastüren bringen mehr Licht in die Räume, und sind auch ein Gestaltungselement.</p>
              <v-expand-transition>
                <div v-if="expanded[6]" class="section-extra">
                  <ul class="section-list">
                    <li>Die Türen bestehen gänzlich aus Sicherheitsglas nach der Norm DIN EN 12150-2. Bei der Fertigung wird das Glas bis zum Weichpunkt erhitzt und unter kontrollierten Bedingungen wieder abgekühlt, dadurch erlangt es eine Eigenspannung mit nahezu 100%iger Planität</li>
                    <li>Die Oberflächen der Türen werden durch eine neu entwickelte NANO-Print-Technologie veredelt</li>
                    <li>Das Design der Türen kann zusätzlich durch einen ansprechenden Rillenschliff optisch hervorgehoben werden. Für derartige geschliffene Motive auf der Glasoberfläche sind Diamant-Werkzeuge mit enorm hohen Drehzahlen nötig</li>
                  </ul>
                </div>
              </v-expand-transition>
              <v-btn
                variant="text"
                class="section-link"
                :append-icon="expanded[6] ? 'mdi-chevron-up' : 'mdi-chevron-down'"
                @click="expanded[6] = !expanded[6]"
              >
                {{ expanded[6] ? 'Weniger' : 'Mehr' }}
              </v-btn>
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
import sliderITmg1 from '@/assets/IT_Slider1.png'
import sliderITmg2 from '@/assets/IT_Slider2.png'
import sliderITmg3 from '@/assets/IT_Slider3.png'



// Lokales Bild muss importiert werden, sonst findet Vite den Pfad nicht
const items = [
  sliderITmg1,
  sliderITmg2,
  sliderITmg3,
]

// Expand/Collapse state per section
const expanded = ref([false, false, false, false, false, false, false])
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



