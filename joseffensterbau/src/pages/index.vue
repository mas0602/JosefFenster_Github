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



  

    
    <!-- Desktop-only Buttons (visible on large desktop only) -->
    <v-row v-if="showButtons" class="btns desktop-only" align="center" justify="center" no-gutters>
      <v-btn class="menu-btn" :to="'/fensterpage'">Fenster</v-btn>
      <v-btn class="menu-btn" :to="'/tuerenpage'">Haustüren</v-btn>
      <v-btn class="menu-btn" href="https://configurator.varialis.net/?bpi=BC27B19A-C106-404F-96C2-60B7AC4C9FD0" target="_blank" rel="noopener">Haustürenkonfigurator</v-btn>
      <v-btn class="menu-btn" :to="'/innentuerenpage'">Innentüren</v-btn>
      <v-btn class="menu-btn" @click="scrollToId('aktionen')">Aktionen</v-btn>
      <v-btn class="menu-btn highlight" :to="'/impressum'">Impressum</v-btn>
    </v-row>

    <!-- Kontakt-Popup (modern, normale Größe) -->
    <v-dialog id="email-dialog" v-model="contactOpen" max-width="480" persistent aria-label="Kontakt per E‑Mail">
      <v-card elevation="8" rounded="lg">
        <v-card-title class="text-h6">Kontakt per E‑Mail</v-card-title>
        <v-card-text>
          <p class="contact-text">Kontaktieren Sie uns per Mail – wir melden uns rasch zurück.</p>
          <!-- E-Mail-Adresse hier anpassen: contactEmail (Prop) -->
          <v-alert type="info" variant="tonal" border="start" class="mb-3" density="comfortable">
            <strong>{{ contactEmail }}</strong>
          </v-alert>

          <!-- Demo-Kontaktformular: E-Mail, Nachricht, Telefonnummer -->
          <v-form @submit.prevent="submitDemo" class="contact-form" aria-label="Kontaktformular (Demo)">
            <v-text-field
              v-model="form.email"
              type="email"
              label="Ihre E‑Mail"
              placeholder="name@beispiel.at"
              variant="outlined"
              density="comfortable"
              :rules="[v => !v || /.+@.+\..+/.test(v) || 'Bitte gültige E‑Mail eingeben']"
            />
            <v-text-field
              v-model="form.phone"
              type="tel"
              label="Telefonnummer"
              placeholder="z. B. +43 664 1234567"
              variant="outlined"
              density="comfortable"
            />
            <v-textarea
              v-model="form.message"
              label="Ihre Nachricht (was Sie möchten)"
              placeholder="Kurz beschreiben, was Sie benötigen…"
              variant="outlined"
              density="comfortable"
              rows="4"
              auto-grow
            />
            <div class="contact-actions">
              <v-spacer />
              <v-btn variant="text" @click="contactOpen = false">Schließen</v-btn>
              <v-btn type="submit" variant="flat">Absenden (Demo)</v-btn>
            </div>
          </v-form>
        </v-card-text>
      </v-card>
    </v-dialog>

    <!-- Floating CTA: Roter Text + Icon-Button -->
    <div class="contact-cta" role="group" aria-label="Kontakt öffnen">
      <button class="contact-fab" type="button" aria-controls="email-dialog" @click="contactOpen = true" aria-label="Kontakt per E‑Mail öffnen">
        ✉️
      </button>
    </div>

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
const navItems = [
  { label: 'Fenster' },
  { label: 'Haustüren' },
  { label: 'Haustürenkonfigurator' },
  { label: 'Innentüren' },
  { label: 'Aktionen' },
  { label: 'Impressum' },
]

// Aktionen-Kategorien (Tabs) und Auswahl
const actionCategories = ['Fensteraktionen', 'Türenaktionen', 'Haustürenaktionen']
const selectedCategory = ref(actionCategories[0])

// Kontakt-Popup Zustand
const contactOpen = ref(false)

// Demo-Formular Zustand
const form = ref({ email: '', phone: '', message: '' })

function submitDemo() {
  // Demo: hier könnte später ein echter Versand erfolgen
  console.log('Demo submit:', { ...form.value })
  contactOpen.value = false
}

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
      { label: 'Aktionen', target: 'aktionen' }
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

// Optional: Popup automatisch öffnen (wenn aktiviert)
onMounted(() => {
  if (props.contactAutoOpen) {
    const delay = Math.max(0, Number(props.contactDelayMs || 0))
    if (delay) setTimeout(() => (contactOpen.value = true), delay)
    else contactOpen.value = true
  }
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
  if (item.label === 'Fenster') {
    router.push('/fensterpage')
  } else if (item.label === 'Haustüren') {
    router.push('/tuerenpage')
  } else if (item.label === 'Haustürenkonfigurator') {
    window.open('https://configurator.varialis.net/?bpi=BC27B19A-C106-404F-96C2-60B7AC4C9FD0', '_blank', 'noopener')
  } else if (item.label === 'Innentüren') {
    router.push('/innentuerenpage')
  } else if (item.label === 'Aktionen') {
    scrollToId('aktionen')
  } else if (item.label === 'Impressum') {
    router.push('/impressum')
  }
}

function handleScroll() {
  showButtons.value = window.scrollY < 80
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
}

.responsive-header { min-height: 72px; }
.header-logo {
  height: auto;
  width: auto;
  object-fit: contain;
}

.spacer { flex: 1; }


.nav-mobile-trigger { display: inline-flex; }

/* --- Breakpoints --- */
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
  .header-logo { max-height: 64px; }
  .menu-btn { font-size: 15px !important; }
}

@media (min-width: 768px) {
  .menu-btn { font-size: 16px !important; }
}

@media (min-width: 1024px) {
  .btns.desktop-only { gap: 32px; top: 28px; right: 32px; }
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

/* --- Kontakt-Popup / FAB --- */
.contact-cta {
  position: fixed;
  right: 16px;
  bottom: 16px;
  display: inline-flex;
  align-items: center;
  gap: 10px;
  z-index: 2147483647;
}
@media (min-width: 768px) {
  .contact-cta { right: 24px; bottom: 24px; }
}
.contact-fab {
  width: 46px;
  height: 46px;
  border-radius: 50%;
  border: 1px solid rgba(214,48,49,0.35);
  background: #ffffff;
  box-shadow: 0 4px 12px rgba(0,0,0,0.10);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  cursor: pointer;
}
.contact-fab:focus-visible { outline: 2px solid currentColor; outline-offset: 3px; }
@media (min-width: 768px) {
  .contact-fab { right: 24px; bottom: 24px; }
}
</style>
