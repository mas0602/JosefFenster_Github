<template>
  <v-app>
    <!-- Fixed Logo (top-left, hides on scroll like the desktop buttons; stays visible in fullscreen) -->
    <div v-show="showButtons" class="fixed-logo" aria-label="Firmenlogo">
      <img :src="logo" alt="Logo" class="header-logo" />
    </div>
    <!-- Responsive Header (hidden on large desktop) -->
    <v-app-bar density="comfortable" flat absolute color="transparent" class="responsive-header">
      <div class="header-container">
        <!-- Only Hamburger Menu for small and laptop widths -->
        <v-menu v-model="menuOpen" location="bottom end" :close-on-content-click="true" content-class="mobile-nav-menu">
          <template #activator="{ props }">
            <v-btn class="nav-mobile-trigger" v-bind="props" icon="mdi-menu" color="white" aria-label="Menü" />
          </template>
          <v-list class="mobile-nav-list" density="default">
            <v-list-item
              v-for="(item, i) in navItems"
              :key="i"
              class="mobile-nav-item"
              @click="onNav(item)"
            >
              <template #prepend>
                <v-icon :icon="item.icon" class="mobile-nav-icon" />
              </template>
              <v-list-item-title class="mobile-nav-title">{{ item.label }}</v-list-item-title>
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



  

    
    <!-- Desktop-only Buttons (visible on large desktop only) -->
    <v-row v-if="showButtons" class="btns desktop-only" align="center" justify="center" no-gutters>
      <v-btn class="menu-btn" :to="'/fensterpage'">Fenster</v-btn>
      <v-btn class="menu-btn" :to="'/tuerenpage'">Haustüren</v-btn>
      <v-btn class="menu-btn" href="https://configurator.varialis.net/?bpi=BC27B19A-C106-404F-96C2-60B7AC4C9FD0" target="_blank" rel="noopener">Haustürenkonfigurator</v-btn>
      <v-btn class="menu-btn" :to="'/innentuerenpage'">Innentüren</v-btn>
      <v-btn class="menu-btn highlight" :to="'/impressum'">Impressum</v-btn>
    </v-row>

    <!-- Footer -->
    <SiteFooter />
  </v-app>
</template>

<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'
import { useRouter } from 'vue-router'
import logo from '@/assets/logo.png'
import SiteFooter from '@/components/SiteFooter.vue'
import sliderImg1 from '@/assets/GPT-SLIDER1.png'
import sliderImg2 from '@/assets/GPT-SLIDER2.png'
import sliderImg3 from '@/assets/GPT-SLIDER3.png'


// Lokales Bild muss importiert werden, sonst findet Vite den Pfad nicht
const items = [
  sliderImg1,
  sliderImg2,
  sliderImg3,
]

const menuOpen = ref(false)
const router = useRouter()
const showButtons = ref(true)
const lastScrollY = ref(0)
const navItems = [
  { label: 'Startseite', icon: 'mdi-home' },
  { label: 'Fenster', icon: 'mdi-window-closed-variant' },
  { label: 'Haustüren', icon: 'mdi-door' },
  { label: 'Haustürenkonfigurator', icon: 'mdi-tune-variant' },
  { label: 'Innentüren', icon: 'mdi-door-sliding' },
  { label: 'Impressum', icon: 'mdi-file-document-outline' },
]

// Aktionen-Kategorien (Tabs) und Auswahl
const actionCategories = ['Fensteraktionen', 'Türenaktionen', 'Haustürenaktionen']
const selectedCategory = ref(actionCategories[0])


// --- Dynamische Inhalte per Props (mit Defaults) ---
// Intro-Text, Link-Leiste und Aktions-Karten können über Props überschrieben werden.
const props = defineProps({
  // Intro-Text oberhalb der Link-Leiste
  introText: {
    type: String,
    default:
      'Wir bieten Ihnen moderne Fenster, Haustüren und Innentüren – hochwertig, energieeffizient und individuell angepasst.'
  },
  // Links der horizontalen Leiste (Label + Ziel-ID)
  links: {
    type: Array,
    default: () => [
      { label: 'Fenster', target: 'fenster' },
      { label: 'Haustüren', target: 'haustueren' },
      { label: 'Innentüren', target: 'innentueren' },
    ]
  },
  // Karten für "Moderne Aktionen der Woche"
  actionCards: {
    type: Array,
    default: () => [
      {
        title: 'Design-Fenster A100',
        description: 'Schlanke Profile, starke Dämmwerte – ideal für Neubau & Sanierung.',
        img: 'https://placehold.co/800x450/png?text=Aktion+1',
        ctaLabel: 'Details',
        ctaHref: '#aktionen'
      },
      {
        title: 'Haustür Modern Line',
        description: 'Sicher, wartungsarm und formschön – inklusive Mehrfachverriegelung.',
        img: 'https://placehold.co/800x450/png?text=Aktion+2',
        ctaLabel: 'Details',
        ctaHref: '#aktionen'
      },
      {
        title: 'Innentür Classic White',
        description: 'Zeitloses Design mit robusten Oberflächen für viel Alltag.',
        img: 'https://placehold.co/800x450/png?text=Aktion+3'
        // Button optional weglassen
      }
    ]
  }
  ,
  // Strukturierte Aktionsdaten je Kategorie (für Tabs)
  actionData: {
    type: Object,
    default: () => ({
      'Fensteraktionen': [
        {
          title: 'Fenster Aktion 1',
          description: 'PVC-Alu, Top U-Wert, kurze Lieferzeit.',
          img: 'https://placehold.co/800x450/png?text=Fenster+1',
          ctaLabel: 'Details',
          ctaHref: '#'
        },
        {
          title: 'Fenster Aktion 2',
          description: 'Schmale Profile, viel Licht, leise Beschläge.',
          img: 'https://placehold.co/800x450/png?text=Fenster+2',
          ctaLabel: 'Details',
          ctaHref: '#'
        },
        {
          title: 'Fenster Aktion 3',
          description: 'Sanierungs-Set inkl. Montagezubehör.',
          img: 'https://placehold.co/800x450/png?text=Fenster+3'
        }
      ],
      'Türenaktionen': [
        {
          title: 'Innentür Aktion 1',
          description: 'Zeitlos weiß, robust, pflegeleicht.',
          img: 'https://placehold.co/800x450/png?text=Innentuer+1',
          ctaLabel: 'Details',
          ctaHref: '#'
        },
        {
          title: 'Innentür Aktion 2',
          description: 'Echtholz-Dekor, leise Schließung.',
          img: 'https://placehold.co/800x450/png?text=Innentuer+2'
        },
        {
          title: 'Innentür Aktion 3',
          description: 'Glastür satiniert inkl. Beschlag.',
          img: 'https://placehold.co/800x450/png?text=Innentuer+3'
        }
      ],
      'Haustürenaktionen': [
        {
          title: 'Haustür Aktion 1',
          description: 'Mehrfachverriegelung, RC2-Option.',
          img: 'https://placehold.co/800x450/png?text=Haustuer+1',
          ctaLabel: 'Details',
          ctaHref: '#'
        },
        {
          title: 'Haustür Aktion 2',
          description: 'Thermo-Kern, Top Dichtungssystem.',
          img: 'https://placehold.co/800x450/png?text=Haustuer+2'
        },
        {
          title: 'Haustür Aktion 3',
          description: 'Modernes Design mit Seitenteil.',
          img: 'https://placehold.co/800x450/png?text=Haustuer+3'
        }
      ]
    })
  }
})
// Gefilterte Karten je nach Kategorie
const filteredCards = computed(() => props.actionData[selectedCategory.value] || [])

// Detail-Dialog Zustand
const detailOpen = ref(false)
const selectedCard = ref(null)
function openCard(card) {
  selectedCard.value = card
  detailOpen.value = true
}
// --- Kontakt-Popup Einstellungen ---

onMounted(() => {
  // Scroll to top when page loads
  window.scrollTo({ top: 0, behavior: 'smooth' })

  lastScrollY.value = window.scrollY || 0
  handleScroll()

  window.addEventListener('scroll', handleScroll, { passive: true })
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

function scrollToId(id) {
  const el = document.getElementById(id)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth', block: 'start' })
  }
}

function onNav(item) {
  menuOpen.value = false
  if (item.label === 'Startseite') {
    router.push('/')
  } else if (item.label === 'Fenster') {
    router.push('/fensterpage')
  } else if (item.label === 'Haustüren') {
    router.push('/tuerenpage')
  } else if (item.label === 'Haustürenkonfigurator') {
    window.open('https://configurator.varialis.net/?bpi=BC27B19A-C106-404F-96C2-60B7AC4C9FD0', '_blank', 'noopener')
  } else if (item.label === 'Innentüren') {
    router.push('/innentuerenpage')
  } else if (item.label === 'Impressum') {
    router.push('/impressum')
  }
}

function handleScroll() {
  const currentY = window.scrollY || 0
  const diff = currentY - lastScrollY.value

  const alwaysShowAtTop = 80
  const threshold = 8 // prevents flicker on tiny scroll changes

  if (currentY <= alwaysShowAtTop) {
    showButtons.value = true
  } else if (diff > threshold) {
    // scrolling down -> hide
    showButtons.value = false
  } else if (diff < -threshold) {
    // scrolling up -> show
    showButtons.value = true
  }

  lastScrollY.value = currentY
}


// no extra helpers needed; links use :to and mobile menu uses router.push
</script>

<style>
/* --- Layout --- */
:root { --page-bg: #fafafa; }
html, body { background: var(--page-bg); }
.slide {
  position: relative;
  /* Use small viewport units for better mobile behavior */
  height: 100svh;
  overflow: hidden;
  isolation: isolate;
  background: var(--page-bg);
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
  justify-content: flex-end;
}

.responsive-header { min-height: 72px; }

.fixed-logo {
  position: fixed;
  top: 16px;
  left: 16px;
  z-index: 2147483647 !important;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  pointer-events: none; /* avoids blocking clicks on buttons */
}

@media (max-width: 479.98px) {
  .fixed-logo { top: 12px; left: 12px; }
  .header-logo { width: clamp(96px, 30vw, 160px); max-height: 56px; }
}

.header-logo {
  height: auto;
  width: auto;
  object-fit: contain;
  max-height: 64px;
}

.spacer { flex: 1; }


.nav-mobile-trigger {
  display: inline-flex;
  padding: 8px !important;
  min-width: 44px;
  min-height: 44px;
  border-radius: 0 !important;
  background: transparent !important;
  border: none !important;
  box-shadow: none !important;
  z-index: 2147483647 !important;
}

.nav-mobile-trigger:hover {
  background: transparent !important;
}

/* --- Mobile menu (glass / liquid, etwas dünner) --- */
.mobile-nav-menu {
  border-radius: 16px;
  overflow: hidden;
  background: transparent !important;
  border: none !important;
  box-shadow: none !important;
  backdrop-filter: blur(14px);
}

.mobile-nav-list {
  background: transparent !important;
  padding: 6px;
  min-width: min(300px, 92vw);
}

.mobile-nav-item {
  border-radius: 12px;
  margin: 4px 4px;
  padding: 4px 6px;
}

.mobile-nav-item:hover {
  background: rgba(255, 255, 255, 0.08);
}

/* Vuetify internal overlays can cancel custom glass backgrounds */
.mobile-nav-item .v-list-item__overlay { opacity: 0 !important; }
.mobile-nav-item .v-list-item__underlay { opacity: 0 !important; }
.mobile-nav-item .v-list-item__content { color: #fff !important; }
.mobile-nav-item .v-list-item-title { color: #fff !important; }

/* Stronger glass effect on the clickable surface */
.mobile-nav-item.v-list-item {
  background: rgba(255, 255, 255, 0.05) !important;
  border: 1px solid rgba(255, 255, 255, 0.10) !important;
}
.mobile-nav-item.v-list-item:hover {
  background: rgba(255, 255, 255, 0.09) !important;
}

.mobile-nav-icon {
  opacity: 0.95;
  color: #fff !important;
}

.mobile-nav-title {
  font-size: 1rem;
  font-weight: 700;
  letter-spacing: 0.01em;
  color: #fff !important;
}

@media (max-width: 479.98px) {
  .mobile-nav-list { min-width: min(280px, 92vw); }
  .mobile-nav-title { font-size: 0.98rem; }
}

@media (max-width: 479.98px) {
  .nav-mobile-trigger { transform: translateY(6px) !important; }
}

/* --- Breakpoints --- */
/* Desktop button row only on large desktop */
@media (max-width: 1279.98px) {
  .desktop-only { display: none !important; }
}

/* Hide hamburger menu on large screens (desktop) */
@media (min-width: 1280px) {
  .nav-mobile-trigger { display: none !important; }
  .responsive-header { display: none !important; }
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
  .header-logo { max-height: 64px; }
  .menu-btn { font-size: 15px !important; }
}

@media (min-width: 768px) {
  .menu-btn { font-size: 16px !important; }
}

@media (min-width: 1024px) {
  .btns.desktop-only { gap: 24px; top: 24px; right: 24px; }
}

/* --- Mobile-friendly: put "Programm:" and "LINKS:" side-by-side on phone --- */
.program-links-head {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

@media (max-width: 600px) {
  .program-links-head {
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
  }

  .program-label,
  .links-label {
    margin: 0;
    padding: 8px 12px;
    border-radius: 999px;
    background: rgba(0,0,0,0.45);
    color: #fff;
    font-weight: 800;
    letter-spacing: 0.02em;
    text-transform: uppercase;
    font-size: 0.9rem;
    line-height: 1;
    backdrop-filter: blur(6px);
  }
}

/* --- Intro & Anchor Nav --- */
.intro { padding: 24px 0; background: var(--page-bg); }
.intro-text {
  font-size: 1.125rem;
  line-height: 1.6;
  text-align: center;
  margin: 0;
}

.anchor-nav {
  background: var(--page-bg);
  border-top: 1px solid rgba(0,0,0,0.08);
  border-bottom: 1px solid rgba(0,0,0,0.08);
}
.anchor-list {
  display: flex;
  flex-wrap: wrap;
  gap: 16px 24px;
  justify-content: center;
  padding: 12px 0;
  margin: 0;
  list-style: none;
}
.anchor-link {
  text-decoration: none;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.02em;
}
.anchor-link:focus-visible { outline: 2px dashed currentColor; outline-offset: 2px; }

/* --- Aktionen der Woche --- */
.actions-of-week {
  padding: 64px 0 48px;
  background: var(--page-bg);
}
.section-title {
  text-align: center;
  margin: 0 0 32px;
  font-weight: 800;
  font-size: 2rem;
  letter-spacing: 0.02em;
}

.actions-tabs { margin: 8px 0 16px; }

.actions-grid {
  display: grid;
  grid-template-columns: repeat(1, minmax(0, 1fr));
  gap: 32px;
}
@media (min-width: 640px) {
  .actions-grid { grid-template-columns: repeat(2, minmax(0, 1fr)); }
}
@media (min-width: 1024px) {
  .actions-grid { grid-template-columns: repeat(3, minmax(0, 1fr)); }
}

.action-card {
  background: white;
  border: none;
  border-radius: 14px;
  overflow: hidden;
  box-shadow: 0 6px 18px rgba(0,0,0,0.08);
  display: flex;
  flex-direction: column;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}
.action-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 24px rgba(0,0,0,0.12);
}
.action-media { display: block; aspect-ratio: 16/9; overflow: hidden; }
.action-media img { width: 100%; height: 100%; object-fit: cover; display: block; }
.action-content {
  padding: 24px;
  display: grid;
  gap: 12px;
}
.action-title { margin: 0; font-size: 1.05rem; }
.action-desc { margin: 0; opacity: 0.9; line-height: 1.5; }
.action-btn { align-self: start; }
/* Roter Button (dunkel) */
.action-btn--red {
  background: #b71c1c !important; /* dunkler Rotton */
  color: #fff !important;
}
.action-btn--red:hover { background: #9a1616 !important; }

/* Detail-Dialog Media */
.detail-media { margin: -8px 0 12px; border-radius: 10px; overflow: hidden; }
.detail-media img { width: 100%; height: auto; display: block; }
.detail-desc { margin: 0; line-height: 1.5; }

/* --- Anker-Ziel-Sektionen (Platzhalter) --- */
.anchor-target { padding: 40px 0; }
.anchor-target h2 { margin-top: 0; }

</style>
