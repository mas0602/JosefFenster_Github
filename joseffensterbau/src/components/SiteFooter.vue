<template>
  <footer class="site-footer">
    <v-container class="footer-container">
      <v-row class="footer-content">
        <!-- Logo Section -->
        <v-col cols="12" md="3" class="footer-logo-col">
          <div class="footer-logo">
            <img src="@/assets/logo.png" alt="JOSEF Fenster & Türen Logo" class="logo-img" />
          </div>
        </v-col>

        <!-- Kontakt Section -->
        <v-col cols="12" md="4" class="footer-section">
          <h3 class="footer-title">KONTAKT:</h3>
          <div class="footer-text">
            <p>
              JOSEF Fenster & Türen<br>
              Joze Glavac<br>
              Hauptstraße 32, A-6840 Götzis<br>
              Tel. <a href="tel:+43552352444" class="footer-link">+43 (0)5523 52444</a><br>
              Fax +43 (0)5523 52446<br>
              Mail: <a href="mailto:office@josef-fenster-tueren.at" class="footer-link">office@josef-fenster-tueren.at</a>
            </p>
            <p class="copyright">© 2025 JOSEF Fenster & Türen</p>
          </div>
        </v-col>

        <!-- Programm Section -->
        <v-col cols="12" md="2" class="footer-section">
          <h3 class="footer-title">PROGRAMM:</h3>
          <ul class="footer-list">
            <li><router-link to="/fensterpage" class="footer-link">Fenster</router-link></li>
            <li><router-link to="/tuerenpage" class="footer-link">Haustüren</router-link></li>
            <li><a href="https://configurator.varialis.net/?bpi=BC27B19A-C106-404F-96C2-60B7AC4C9FD0" target="_blank" rel="noopener" class="footer-link">Haustürkonfigurator</a></li>
            <li><router-link to="/innentuerenpage" class="footer-link">Innentüren</router-link></li>
          </ul>
        </v-col>

        <!-- Links Section -->
        <v-col cols="12" md="3" class="footer-section">
          <h3 class="footer-title">LINKS:</h3>
          <ul class="footer-list">
            <li><router-link to="/impressum" class="footer-link">Impressum</router-link></li>
            <li><router-link to="/rechtliche-hinweise" class="footer-link">Rechtliche Hinweise</router-link></li>
            <li><router-link to="/datenschutzrichtlinie" class="footer-link">Datenschutzrichtlinie</router-link></li>
          </ul>
        </v-col>
      </v-row>
    </v-container>
  </footer>
</template>

<script setup>
// No script needed for this component
</script>

<style scoped>
.site-footer {
  background-color: #f5f5f7;
  padding: 40px 0 30px;
  margin-top: 0;
}

.footer-container {
  max-width: 1200px;
}

.footer-content {
  align-items: flex-start;
}

.footer-logo-col {
  display: flex;
  align-items: center;
}

.footer-logo {
  display: flex;
  align-items: center;
}

.logo-img {
  max-width: 150px;
  height: auto;
}

.footer-section {
  padding: 0 16px;
}

.footer-title {
  font-size: 16px;
  font-weight: 700;
  color: #1d1d1f;
  margin: 0 0 16px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.footer-text {
  font-size: 14px;
  line-height: 1.6;
  color: #1d1d1f;
}

.footer-text p {
  margin: 0 0 12px;
}

.footer-text p:last-child {
  margin-bottom: 0;
}

.copyright {
  margin-top: 16px !important;
  font-size: 14px;
  color: #1d1d1f;
}

.footer-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-list li {
  margin-bottom: 8px;
  position: relative;
  padding-left: 16px;
}

.footer-list li::before {
  content: "›";
  position: absolute;
  left: 0;
  color: #d63031;
  font-weight: bold;
  font-size: 18px;
}

.footer-link {
  color: #1d1d1f;
  text-decoration: none;
  transition: color 0.2s ease;
  font-size: 14px;
}

.footer-link:hover {
  color: #d63031;
}

.footer-text .footer-link {
  color: #d63031;
  text-decoration: underline;
}

.footer-text .footer-link:hover {
  opacity: 0.8;
}

/* Responsive */
@media (max-width: 959.98px) {
  .site-footer {
    padding: 30px 0 20px;
  }

  .footer-section {
    padding: 0;
    margin-bottom: 32px;
  }

  .footer-logo-col {
    margin-bottom: 24px;
  }

  .logo-img {
    max-width: 120px;
  }
}
</style>
