<template>
  <v-app>
    <v-main class="pa-0">
      <!-- Compact hero slideshow -->
      <section class="hero">
        <v-carousel class="hero-carousel" hide-delimiters show-arrows="hover" cycle height="60svh" transition="fade-transition">
          <v-carousel-item v-for="i in 3" :key="i">
            <v-img src="" alt="Hero Slide" cover class="hero-img" />
            <div class="hero-overlay">
              <h2 class="hero-title">Innentüren Highlights {{ i }}</h2>
              <p class="hero-sub">Form, Material und Funktion für jedes Raumkonzept.</p>
            </div>
          </v-carousel-item>
        </v-carousel>
      </section>

      <!-- Long-scroll stacked sections (Apple-style) -->
      <section class="section section--light">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="6" class="section-media">
              <v-img src="" alt="Innentüren Urban" cover class="section-img" />
            </v-col>
            <v-col cols="12" md="5" class="section-body">
              <h3 class="section-title red">Innentüren Urban</h3>
              <p class="section-text">Schlichte Formen, klare Linien. Harmonieren mit moderner Architektur und schaffen ruhige Innenräume.</p>
              <v-btn variant="text" class="section-link" append-icon="mdi-chevron-right">Mehr…</v-btn>
            </v-col>
          </v-row>
        </v-container>
      </section>

      <section class="section section--alt">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="5" class="section-body order-md-1">
              <h3 class="section-title red">Innentüren Natura</h3>
              <p class="section-text">Natürliches Holz und warme Oberflächen für behagliche, zeitlose Wohnwelten.</p>
              <v-btn variant="text" class="section-link" append-icon="mdi-chevron-right">Mehr…</v-btn>
            </v-col>
            <v-col cols="12" md="6" class="section-media order-md-2">
              <v-img src="" alt="Innentüren Natura" cover class="section-img" />
            </v-col>
          </v-row>
        </v-container>
      </section>

      <section class="section section--light">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="6" class="section-media">
              <v-img src="" alt="Innentüren Klassik" cover class="section-img" />
            </v-col>
            <v-col cols="12" md="5" class="section-body">
              <h3 class="section-title red">Innentüren Klassik</h3>
              <p class="section-text">Handwerkliche Details und langlebige Materialien – klassische Eleganz für viele Stile.</p>
              <v-btn variant="text" class="section-link" append-icon="mdi-chevron-right">Mehr…</v-btn>
            </v-col>
          </v-row>
        </v-container>
      </section>

      <section class="section section--alt">
        <v-container class="section-container">
          <v-row align="center" justify="space-between">
            <v-col cols="12" md="5" class="section-body order-md-1">
              <h3 class="section-title red">Innentüren Ganzglas</h3>
              <p class="section-text">Mehr Licht und optische Weite. Hochwertige Glaslösungen mit präziser Verarbeitung.</p>
              <v-btn variant="text" class="section-link" append-icon="mdi-chevron-right">Mehr…</v-btn>
            </v-col>
            <v-col cols="12" md="6" class="section-media order-md-2">
              <v-img src="" alt="Innentüren Ganzglas" cover class="section-img" />
            </v-col>
          </v-row>
        </v-container>
      </section>
    </v-main>
  </v-app>

  <!-- Desktop-only Buttons (visible on large desktop only) -->
  <v-row class="btns desktop-only" align="center" justify="center" no-gutters>
    <v-btn class="menu-btn" :to="'/'">Startseite</v-btn>
    <v-btn class="menu-btn" :to="'/fensterpage'">Fenster</v-btn>
    <v-btn class="menu-btn" :to="'/tuerenpage'">Haustüren</v-btn>
    <v-btn class="menu-btn" href="https://configurator.varialis.net/?bpi=BC27B19A-C106-404F-96C2-60B7AC4C9FD0" target="_blank" rel="noopener">Haustürenkonfigurator</v-btn>
    <v-btn class="menu-btn" :to="'/innentuerenpage'">Innentüren</v-btn>
    <v-btn class="menu-btn highlight">Impressum</v-btn>
  </v-row>
  
</template>

<script setup>
// No logic yet; images and links can be wired later
</script>

<style>
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
.section { padding: 56px 0; }
.section--light { background: #fff; }
.section--alt { background: #f5f5f7; }
.section-container { max-width: 1200px; }
.section-img { height: 360px; background: #e5e7eb; }
.section-title { font-size: 28px; font-weight: 800; margin: 0 0 12px; text-transform: uppercase; }
.section-title.red { color: #d63031; }
.section-text { color: #4b5563; margin: 0 0 12px; }
.section-link { color: #6b7280 !important; text-transform: none !important; }

/* Ordering helpers for alternating layout */
@media (min-width: 960px) {
  .order-md-1 { order: 1; }
  .order-md-2 { order: 2; }
}

/* Responsive tweaks */
@media (max-width: 959.98px) {
  .hero-title { font-size: 22px; }
  .section { padding: 40px 0; }
  .section-img { height: 240px; }
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
</style>



