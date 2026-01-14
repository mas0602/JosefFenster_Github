<template>
  <v-app>
    <!-- Responsive Header (hidden on large desktop) -->
    <v-app-bar density="comfortable" flat color="transparent" class="responsive-header">
      <div class="header-container">
        <router-link to="/">
          <img :src="logo" alt="Logo" class="header-logo" />
        </router-link>
        <div class="spacer" />
        <!-- Only Hamburger Menu for small and laptop widths -->
        <v-menu v-model="menuOpen" location="bottom end" :close-on-content-click="true">
          <template #activator="{ props }">
            <v-btn class="nav-mobile-trigger" v-bind="props" icon="mdi-menu" color="black" aria-label="Menü" />
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
      <!-- Kontaktdaten Section -->
      <section id="kontakt" class="section section--alt">
        <v-container class="section-container">
          <v-row>
            <v-col cols="12" md="5" class="contact-info">
              <h2 class="section-title">KONTAKTDATEN</h2>
              <div class="content-block">
                <p class="content-text">
                  JOSEF Fenster & Türen<br>
                  Joze Glavac<br>
                  Hauptstraße 32<br>
                  A-6840 Götzis<br>
                  Tel. <a href="tel:+43552352444" class="content-link">+43 (0)5523 52444</a><br>
                  Fax +43 (0)5523 52446<br>
                  Mail: <a href="mailto:office@josef-fenster-tueren.at" class="content-link">office@josef-fenster-tueren.at</a><br>
      
                </p>
              </div>
            </v-col>
            <v-col cols="12" md="7" class="map-container">
              <h2 class="section-title">Standort</h2>
              <div class="map-wrapper">
                <iframe
                  src="https://www.google.com/maps?q=Hauptstra%C3%9Fe+32,+6840+G%C3%B6tzis,+%C3%96sterreich&output=embed"
                  width="100%"
                  height="280"
                  style="border:0;"
                  allowfullscreen=""
                  loading="lazy"
                  referrerpolicy="no-referrer-when-downgrade"
                  class="map-iframe"
                ></iframe>
                <p class="map-link">
                  <a
                    href="https://maps.google.de/maps?f=q&source=embed&hl=de&geocode=&q=Hauptstra%C3%9Fe+32+6840+G%C3%B6tzis,+%C3%96sterreich"
                    target="_blank"
                    rel="noopener"
                    class="content-link"
                  >
                    Größere Kartenansicht
                  </a>
                </p>
              </div>
            </v-col>
          </v-row>
        </v-container>
      </section>



      <!-- Verkaufs- und Lieferbedingungen Section -->
      <section class="section section--light">
        <v-container class="section-container">
          <h2 class="section-title">RECHTLICHE INFORMATIONEN</h2>
          <v-expansion-panels variant="accordion" class="legal-panels">
            <v-expansion-panel>
              <v-expansion-panel-title>
                Verkaufs- und Lieferbedingungen
              </v-expansion-panel-title>
              <v-expansion-panel-text>
                <div class="content-block">
                  <div class="content-text">
                    <p>
                      <strong>1. ALLGEMEINES</strong><br>
                      1.1 Vertragsinhalt ist nur, was auf diesem Vertragsformular schriftlich festgehalten od. von uns schriftlich bestätigt ist.<br>
                      1.2 Unsere Vertreter sind berechtigt, für uns Vertragsabschlüsse vorzunehmen; sie sind jedoch nicht inkassoberechtigt. An unser Angebot sind wir 14 Tage ab Ausstellungsdatum gebunden. Werden an uns Angebote gerichtet, so ist der Besteller daran 8 Tage ab Zugang des Angebotes gebunden.<br>
                      1.3 Einkaufsbedingungen des Bestellers verpflichten uns nur dann, wenn wir deren Geltung schriftlich anerkannt haben.<br>
                      1.4 Ergänzend gelten die „Qualitätsrichtlinien Fenster, Außentüren und Fassadenelemente" der „Plattform Fenster und Fensterfassade" der Österreichischen Bundeswirtschaftskammer in der im Vertragsabschlusszeitpunkt gültigen Fassung.<br>
                      1.5 Sollten einzelne Bestimmungen dieser Verkaufs- u. Lieferbedingungen unwirksam sein, so bleiben die übrigen Bestimmungen wirksam. Die unwirksame Bestimmung wird durch eine rechtlich zulässige Bestimmung ersetzt, die dem wirtschaftlichen Zweck der unwirksamen Bestimmung möglichst nahe kommt und die redliche Vertragsparteien in Kenntnis der Unwirksamkeit der zu ersetzenden Bestimmung vereinbart hätten.<br>
                      <br>
                      <strong>2. LIEFERFRIST UND LIEFERUNG</strong><br>
                      2.1 Die in der Bestellung angegebene voraussichtliche Lieferfrist ist nicht verbindlich. Eine verbindliche Lieferfrist kann erst nach Vorplanung und Auftragserfassung durch uns im Werk, spätestens jedoch 6 Wochen nach der Bestellung zugesagt werden (ausgenommen: Planmaßaufträge). Die Lieferfrist verlängert sich um jenen Zeitraum, in dem der Besteller Angaben, die er nach der getroffenen Vereinbarung uns gegenüber zu machen hat und die für unsere Lieferung erforderlich sind, nicht oder nicht vollständig macht.<br>
                      2.2 Änderungen einer Bestellung werden von uns akzeptiert, sofern sie für uns durchführbar sind, können aber Preis- und Lieferterminanpassungen zur Folge haben.<br>
                      2.3 Sofern nicht ausdrücklich Gesamtlieferung vereinbart ist, sind wir berechtigt, die Lieferung auch in Teilen durchzuführen.<br>
                      2.4 Schadenersatz wegen Nichterfüllung oder Verspätung ist nur bei grober Fahrlässigkeit oder Vorsatz möglich. Sofern ausdrücklich eine Pönale vereinbart wurde, ist diese mit höchstens 5 % der Nettoauftragssumme insgesamt begrenzt.<br>
                      2.5 Unvorhergesehene, von uns nicht zu vertretende Lieferhindernisse (Streik, Ausfall von Materialanlieferungen, Unterbindung der Verkehrswege oder sonstige Fälle von höherer Gewalt usw.) berechtigen uns zu einer Verlängerung der Lieferfrist um höchstens zwei Monate. Im übrigen gilt nach Ablauf der Lieferfrist der 2.4 mit der Maßgabe, dass eine etwaige Pönale zur Gänze entfällt.<br>
                      2.6 Wir liefern bis zur ersten, leicht erreichbaren, ebenerdigen, geeigneten Lagerfläche, die vom Besteller vorzubereiten und zur Verfügung zu stellen ist. Vertragen und Montieren nur bei schriftlicher Vereinbarung gegen Verrechnung.<br>
                      2.7 Für die freie und gefahrlose Zufahrt (mit 16t LKW, Höhe 4m) bis unmittelbar zur Abladefläche und für die sorgfältige Lagerung der Elemente insbesondere im Hinblick auf Diebstahl, Feuchtigkeitsschäden und Beschädigungen, hat der Besteller zu sorgen. Bei Elementen über 150kg Gewicht hat der Besteller für geeignete Helfer beim Abladen zu sorgen.<br>
                      2.8 Der Besteller hat dafür Sorge zu tragen, dass er oder eine Vertretungsperson die Lieferung übernimmt. Die Ware ist bei Ablieferung auf Vollständigkeit zu überprüfen. Beschädigte Verpackungen, Kratzer, Druckstellen, Dellen, Abschürfungen etc. sind bei nicht vollständig verpackter Ware (insbesondere Fenster, Klappläden, Rollläden, etc.) sofort bei Ablieferung bei sonstigem Anspruchsverlust zu reklamieren.<br>
                      2.9 Nimmt der Besteller die vertragsmäßig bereitgestellte Ware zum vertraglich vereinbarten Zeitpunkt nicht an, sind wir berechtigt vollständige Zahlung zu verlangen und die Einlagerung der Ware und allfällige Neuzustellung auf Kosten und Gefahr des Bestellers vorzunehmen.<br>
                      <br>
                      <strong>3. GEWÄHRLEISTUNG UND SCHADENERSATZ</strong><br>
                      3.1 Der Besteller hat bei sonstigem Anspruchsverlust jede Lieferung unverzüglich, jedenfalls aber vor Einbau oder Weiterverarbeitung auf sichtbare Mängel zu überprüfen und festgestellte Mängel schriftlich in detaillierter Weise ebenso unverzüglich, spätestens binnen 10 Tagen, zu rügen. Auf die Einrede der mangelnden Rüge können wir uns im Streitfall auch dann berufen, wenn wir sie außergerichtlich nicht erhoben haben.<br>
                      3.2 Verdeckte Mängel sind bei sonstigem Anspruchsverlust unverzüglich nach ihrer Entdeckung zu rügen, sofern die Rüge innerhalb der Gewährleistungsfrist erfolgt.<br>
                      3.3 Wir können Gewährleistungsansprüche nach unserer Wahl durch Verbesserung, Austausch oder Preisminderung erfüllen. Der Besteller verzichtet auf die Wandlung des Vertrages. Die Verbesserung erfolgt nach unserer Wahl am Lieferort oder im Werk.<br>
                      3.4 Schadenersatzansprüche aus Sach- und Vermögensschäden uns gegenüber sind ausgeschlossen, sofern uns nicht grobe Fahrlässigkeit oder Vorsatz trifft. Die Höhe der Schadenersatzansprüche ist mit dem Wert der gelieferten Ware (Teilware) beschränkt. Für reine Vermögensschäden haften wir nicht.<br>
                      3.5 3.4 gilt auch für sämtliche vorvertraglichen Schutzbestimmungen unsererseits, etwa Warnpflicht oder Aufklärungspflicht.<br>
                      3.6 Die Gewährleistungsfrist beträgt 6 Monate ab Lieferung und beginnt mit dem Tag der Anlieferung unserer Produkte an der vereinbarten Lieferadresse. Die Geltung von § 924 Satz 2 ABGB wird ausgeschlossen. Ersatzlieferungen oder Mängelbehebungen verlängern, hemmen oder unterbrechen die Gewährleistungsfrist nicht. Rückgriffsansprüche nach § 933b ABGB gegen uns sind ausgeschlossen. Die Geltendmachung von Mängeln berechtigt den Besteller nicht zur Einrede des nicht erfüllten Vertrages und zur Änderung von Zahlungsbedingungen.<br>
                      3.7 Für Verbraucher gilt die gesetzliche Gewährleistung.<br>
                      <br>
                      <strong>4. ZAHLUNG</strong><br>
                      4.1 Bei schuldhaftem Zahlungsverzug werden wir die gesetzlichen Verzugszinsen berechnen. Überdies sind uns diesfalls sämtliche zur zweckentsprechenden Rechtsverfolgung erforderlichen, in einem angemessenen Verhältnis zur offenen Forderung stehenden Mahn- und Anwaltskosten zu ersetzen<br>
                      4.2 Der Besteller erklärt sich damit einverstanden, dass alle Zahlungen die er leistet, zuerst auf Spesen und Kosten, dann auf Zinsen und schließlich auf das Kapital verrechnet werden.<br>
                      4.3 Bei Zahlungsverzug oder Hervorkommen solcher Umstände in den wirtschaftlichen Verhältnissen des Bestellers, die unsere Forderungen als nicht mehr ausreichend gesichert erscheinen lassen (Eröffnung eines Insolvenzverfahrens oder Abweisung der Eröffnung mangels ausreichenden Vermögens, Bewilligung eines Exekutionsverfahrens wegen offener Zahlungsverpflichtung), sind wir berechtigt, alle noch offenen Forderungen bei gleichzeitiger Einstellung jeder weiteren Lieferung sofort fällig zu stellen.<br>
                      <br>
                      <strong>5. EIGENTUMSVORBEHALT</strong><br>
                      5.1 Alle Waren werden unter Eigentumsvorbehalt geliefert. Sie bleiben bis zur vollständigen Bezahlung der offenen Forderung unser Eigentum, auch wenn sie bereits montiert sind.<br>
                      5.2 In Falle der Geltendmachung unseres Eigentumsvorbehalts ermächtigt uns der Besteller schon jetzt, den Besitz unserer Ware ohne gerichtliche Hilfe zu entziehen und gewährt uns zu diesem Zweck jederzeitigen freien Zutritt zu unserer Ware.<br>
                      5.3 Der Besteller hat die Pflicht, während der Dauer des Eigentumsvorbehaltes die Ware in ordnungsgemäßem Zustand zu halten und uns von allfälligen exekutiven Maßnahmen unverzüglich zu informieren.<br>
                      5.4 Der Besteller darf die unter Eigentumsvorbehalt gelieferte Ware nur im ordnungsgemäßen Geschäftsverkehr und solange er uns gegenüber nicht in Verzug ist, veräußern. Dabei ist er verpflichtet, seinerseits Eigentumsvorbehalt mit dem Drittkäufer zu vereinbaren und tritt diesen schon jetzt an uns ab. Die durch den Weiterverkauf der Ware entstehende Forderung gegen Dritte werden vom Besteller schon jetzt mit allen Nebenabreden bis zur Höhe der uns zustehenden Kaufpreisforderung samt Zinsen und Kosten zahlungshalber an uns abgetreten, wobei wir berechtigt sind, die Abtretung der Forderung offenzulegen.<br>
                      5.5 Der Besteller verzichtet auf die Möglichkeit der Aufrechnung. Das gilt nicht gegenüber Verbraucher für den Fall unserer Zahlungsunfähigkeit für Gegenforderungen, die im rechtlichen Zusammenhang mit unserer Forderung stehen, gerichtlich festgestellt oder von uns anerkannt sind. In diesen Fällen besteht für Verbraucher die Möglichkeit zur Aufrechnung.<br>
                      5.6 Reklamation berechtigt nicht zur Rückbehaltung des Rechnungsbetrages. Für Verbraucher gilt, dass diese nur dann Ihre Zahlung verweigern können, wenn wir die Lieferung nicht vertragsgemäß erbracht haben oder die Erbringung durch eine Verschlechterung der Vermögensverhältnisse, die ihnen zum Zeitpunkt des Vertragsabschlusses nicht bekannt waren bzw. nicht bekannt sein mussten, gefährdet ist.<br>
                      <br>
                      <strong>6. PREISGARANTIE, STORNO, RÜCKTRITTSRECHT</strong><br>
                      6.1 Wir gewähren Preisgarantie bei Auslieferung innerhalb 6 Monaten ab Bestelldatum. Erfolgt die Lieferung aus Gründen, die in der Sphäre des Bestellers liegen, nach diesem Zeitpunkt, werden die zum Lieferzeitpunkt aktuellen Preise verrechnet.<br>
                      6.2 Bei Bestellung „auf Abruf" ist der gewünschte Liefertermin mindestens 4 Monate vorher bekanntzugeben. Wird die Ware nicht zur Lieferung innerhalb von 2 Jahren ab Bestelldatum abgerufen, so können wir vom Vertrag zurücktreten und eine Stornogebühr in Höhe von 30% der Auftragssumme verrechnen.<br>
                      6.3 Im Falle eines unberechtigten Vertragsrücktrittes durch den Besteller sind wir berechtigt, entweder den erlittenen Schaden und entgangenen Gewinn, oder eine Stornogebühr von 30% zu verlangen, ohne dass wir einen konkreten Schadensnachweis zu erbringen haben.<br>
                      6.4 Die Stornogebühr unterliegt nicht dem richterlichen Mäßigungsrecht.<br>
                      <br>
                      <strong>7. ERFÜLLUNGSORT UND GERICHTSSTAND</strong><br>
                      7.1 Erfüllungsort für beide Teile ist Kopfing. Für alle sich ergebenden Rechtsstreitigkeiten ist das sachlich zuständige Gericht in A-6850 Dornbirn zuständig.<br>
                      7.2 Anzuwenden ist österreichisches Recht. Die Geltung des UN-Kaufrechtes wird ausgeschlossen.<br>
                      <br>
                      <strong>8. INFORMATIONEN ZUR AUSÜBUNG DES WIDERRUFSRECHTS FÜR KONSUMENTEN:</strong><br>
                      8.1 Rücktrittsrecht:<br>
                      Haben Sie ihre Vertragserklärung nicht in den von uns für unsere geschäftlichen Zwecke dauernd benützten Räumen abgegeben, so können Sie von Ihrem Vertragsantrag oder vom Vertrag zurücktreten.<br>
                      8.2 In diesem Fall haben Sie das Recht, binnen 14 Tagen ohne Angabe von Gründen den Vertrag zu widerrufen. Die Rücktrittsfrist beträgt 14 Tage ab dem Tag an dem Sie oder ein von Ihnen benannter Dritter, der nicht Beförderer ist, die letzte Ware in Besitz genommen hat. Im Falle eines Dienstleistungsvertrages beginnt die Rücktrittsfrist ab dem Tag des Vertragsabschlusses.<br>
                      8.3 Ausnahmen vom Rücktrittsrecht:<br>
                      Das Rücktrittsrecht gilt jedoch insbesondere nicht bei der Bestellung von Waren, die nach Ihren Kundenspezifikationen angefertigt werden oder eindeutig auf die persönlichen Bedürfnisse zugeschnitten sind.
                      Verlangen Sie ausdrücklich – nach Bestätigung Ihrer Kenntnis vom Verlust des Rücktrittsrechtes – dass wir vor Ablauf der Rücktrittsfrist mit der Ausführung der Dienstleistung beginnen sollen, verlieren Sie bei vollständiger Leistungserbringung noch vor Ablauf der Rücktrittsfrist das Rücktrittsrecht.<br>
                      Sie haben weiters kein Rücktrittsrecht bei Verträgen über dringende Reparatur- oder Instandhaltungsarbeiten, bei denen Sie uns ausdrücklich zu einem Besuch zur Ausführung dieser Arbeiten aufgefordert haben. Erbringen wir bei einem solchen Besuch weitere Dienstleistungen, die Sie nicht ausdrücklich verlangt haben, oder liefern Waren, die bei der Instandhaltung oder Reparatur nicht unbedingt als Ersatzteile benötigt werden, so steht Ihnen hinsichtlich dieser zusätzlichen Dienstleistungen oder Waren das Rücktrittsrecht zu.<br>
                      8.4 Um das Rücktrittsrecht auszuüben, muss JOSEF Fenster & Türen, Joze Glavac, Hauptstraße 32 A-6840 Götzis, Tel. +43 (0)5523 52444, Fax +43 (0)5523 52446, Mail: office@josef-fenster-tueren.at mittels einer eindeutigen Erklärung (z.B. ein mit der Post versandter Brief, Telefax oder E-Mail oder Rücktrittsformular) über den Entschluss, den Vertrag zu widerrufen, informiert werden. Zur Wahrung der Rücktrittsfrist reicht es aus, dass die Mitteilung über die Ausübung des Rücktrittsrechts vor Ablauf der Rücktrittsfrist abgesendet wird.<br>
                      8.5 Folgen des Rücktritts:<br>
                      Wird der Vertrag widerrufen, haben wir alle erhaltenen Zahlungen einschließlich der Lieferkosten (mit Ausnahme der zusätzlichen Kosten, die sich daraus ergeben, dass eine andere Art der Lieferung als die von uns angebotene, günstige Standardlieferung gewählt wurde), unverzüglich und spätestens binnen 14 Tagen ab dem Tag zurückzuzahlen, an dem die Mitteilung über den Rücktritt des Vertrags bei uns eingegangen ist. Wir können jedoch die Rückzahlung verweigern, bis wir die Waren wieder zurückerhalten haben oder bis der Nachweis erbracht wurde, dass die Waren zurückgesandt wurden, je nachdem, welches der frühere Zeitpunkt ist.<br>
                      8.6 Sie tragen die Kosten der Rücksendung der Ware.<br>
                      <br>
                      <br>
                      <strong>WICHTIGE HINWEISE ZU UNSEREN PRODUKTEN</strong><br>
                      <br>
                      Holz ist ein Naturprodukt. Daher sind leichte Farbunterschiede zu unseren Mustern, beim Zusammenbau einzelner Profile, bei Nachbestellungen, sowie leichte Unebenheiten des Holzes bedingt durch seine Struktur, unvermeidbar und kein Mangel, sondern Zeichen der Echtheit des Werkstoffes Holz. Auch bei Kunststoff und bei Aluminium können werkstoff- und herstellungsbedingt, leichte Farbschwankungen auftreten.
                      Elemente aus Holz die ohne Endbeschichtung (Dickschichtlasur) bestellt werden, werden ohne Zwischenschliff geliefert. Eine geeignete Oberflächenbeschichtung ist unverzüglich vorzunehmen. Für Schäden aus nicht erfolgter oder mangelhafter Oberflächenbehandlung haften wir nicht.
                      Bei Außenbauteilen und Verglasungen kann es bedingt durch äußere Einflüsse zu Tauwasserbildung (z.B. an Rahmen, an beiden Seiten der Verglasung, an Beschlägen, etc.) kommen. Diese äußeren Einflüsse liegen nicht in unserem Bereich, daher stellt Tauwasserbildung keinen Mangel dar.
                      Einbausprossen im Isolierglas können beweglich sein bzw. teilweise am Glas anliegen. Bei Erschütterungen der Glaseinheit kann es dadurch zu leichtem Klirren kommen ohne das dies einen Mangel darstellt.
                      Isolierglas kann auch ohne sichtbare Einflüsse spontan brechen. Tritt dies innerhalb 6 Monate nach Lieferung auf, wird dies von uns kostenlos behoben, wenn keine mechanische Einwirkung sichtbar ist. Nach dieser Zeit - bis zum Ablauf der Gewährleistungsfrist - erfolgt eine Erledigung nur dann kostenlos, wenn das Vorliegen eines Mangels bei Lieferung bewiesen ist.<br>
                      <br>
                      <strong>WICHTIG: BAUTEILE AUS HOLZ DÜRFEN NICHT EINER RAUMLUFTFEUCHTIGKEIT VON ÜBER 55% AUSGESETZT WERDEN!</strong> <br>
                      <strong>KONDENSWASSER AM GLASRAND IST EIN ZEICHEN ZU HOHER RAUMLUFTFEUCHTIGKEIT.</strong><br>
                      <br>
                      Nichtbeachtung führt zu dauerhaften Schäden an Holzverbindungen, Glashalteleisten und Oberfläche!
                      Wir weisen darauf hin, dass die nach dem Fenstereinbau auftretende Durchbiegung von Überlagern, Stürzen und Decken im Bereich unserer Bauelemente, unabhängig von der Breite, max. 3 mm betragen darf. Andernfalls kommt es zu Funktionsstörungen oder Beschädigungen. Bei Überschreitung dieses Wertes gehen sämtliche hieraus resultierenden Beeinträchtigungen und Schäden (z.B. Glasbruch, etc.) zu Lasten des Bestellers.
                    </p>
                  </div>
                </div>
              </v-expansion-panel-text>
            </v-expansion-panel>

            <v-expansion-panel>
              <v-expansion-panel-title>
                Rechtliche Hinweise
              </v-expansion-panel-title>
              <v-expansion-panel-text>
                <div class="content-block">
                  <div class="content-text">
                    <p>
                      <strong>Nutzungsbedingungen der Website</strong><br>
                      Alle Inhalte unserer Homepage sind urheberrechtlich geschützt. Wir gestatten ausdrücklich die Nutzung aller Daten für den privaten, nicht kommerziellen Gebrauch. Bei Vervielfältigung ist auf die Urheber- und Eigentumsrechte der JOSEF Fenster & Türen GmbH ausdrücklich hinzuweisen. Inhalte dürfen in keiner Weise verändert werden und ohne schriftliche Genehmigung nicht auf anderen Internetseiten oder vernetzten Rechnern genutzt werden. Jegliche Nutzung für öffentliche oder kommerzielle Zwecke bedarf der Zustimmung der JOSEF Fenster & Türe GmbH. Ein Verstoß gegen diese Bedingungen verpflichtet zur sofortigen Vernichtung aller Inhalte. Die Geltendmachung weiterer Schadensersatzansprüche bleibt vorbehalten.<br>
                      <br>
                      <strong>Gewährleistung der Informationen</strong><br>
                      Die Informationen auf unseren Internetseiten werden mit größter Sorgfalt erstellt. Die JOSEF Fenster & Türe GmbH übernimmt jedoch keine Gewähr für deren Vollständigkeit oder Geeignetheit für bestimmte Verwendungszwecke. Die Nutzung der auf den Internetseiten zur Verfügung gestellten Inhalte erfolgt auf alleinige Gefahr des Nutzers.<br>
                      <br>
                      <strong>Internetdienste & Querverweise</strong><br>
                      Unsere Webseiten enthalten auch Querverweise (LINKS) zu Webseiten anderer Anbieter. Für fremde Inhalte, die über solche Querverweise (LINKS) erreichbar sind, ist die JOSEF Fenster & Türe GmbH nicht verantwortlich. Das fremde Angebot wurde bei der erstmaligen Verlinkung auf rechtswidrige Inhalte überprüft. Erst wenn wir feststellen oder darauf hingewiesen werden, dass ein Angebot rechtswidrigen Inhalt aufweist, wird dieser Querverweis (LINK) aufgehoben, soweit dies technisch möglich und zumutbar ist. Wir verwenden in unseren Webseiten Cookies & ein Sessionmanagement, die die Benutzung unserer Online Angebote erleichtern. Unsere Cookies enthalten keine personenspezifischen Informationen, weder Ihre Mail-Adresse, noch sagen Sie uns, wer Sie sind.
                    </p>
                  </div>
                </div>
              </v-expansion-panel-text>
            </v-expansion-panel>

            <v-expansion-panel>
              <v-expansion-panel-title>
                Datenschutzrichtlinie
              </v-expansion-panel-title>
              <v-expansion-panel-text>
                <div class="content-block">
                  <div class="content-text">
                    <p>
                      <strong>Verantwortlicher</strong><br>
                      Diese Website wird von der JOSEF Fenster & Türe GmbH, Hauptstraße 32, A-6840 Götzis betrieben. Unsere vollständigen Daten finden sie im Impressum. Wir nehmen den Schutz ihrer persönlichen Daten sehr ernst. Wir behandeln ihre personenbezogenen Daten vertraulich und entsprechend der gesetzlichen Datenschutzvorschriften sowie dieser Datenschutzerklärung. Ihre Daten werden ohne ihre ausdrückliche Zustimmung nicht an andere Empfänger weitergegeben.<br>
                      <br>
                      <strong>Erhebung, Verarbeitung und Nutzung personenbezogener Daten</strong><br>
                      Erhoben werden jene Daten, die Sie selbst durch eine Kontaktformular zur Verfügung stellen. Es besteht keine Verpflichtung, jene Daten, um deren Angabe wir Sie auf unserer Website bitten, tatsächlich anzugeben. Wenn Sie dies jedoch nicht tun, wird es Ihnen nicht möglich sein, alle Funktionen der Website zu nutzen.<br>
                      <br>
                      <strong>Kontaktformular</strong><br>
                      Wenn sie per Formular auf der Website oder per office@josef-fenster-tueren.at mit uns Kontakt aufnehmen, werden ihre angegebenen Daten zwecks Bearbeitung der Anfrage bei uns gespeichert.<br>
                      <br>
                      <strong>Cookies</strong><br>
                      Unsere Website verwendet so genannte Cookies. Dabei handelt es sich um kleine Textdateien, die mit Hilfe des Browsers auf ihrem Endgerät abgelegt werden. Sie richten keinen Schaden an. Wir nutzen Cookies dazu, unser Angebot nutzerfreundlich zu gestalten. Einige Cookies bleiben auf ihrem Endgerät gespeichert, bis Sie diese löschen. Sie ermöglichen es uns, ihren Browser beim nächsten Besuch wiederzuerkennen. Wenn Sie dies nicht wünschen, so können sie ihren Browser so einrichten, dass er sie über das Setzen von Cookies informiert und Sie dies nur im Einzelfall erlauben. Bei der Deaktivierung von Cookies kann die Funktionalität unserer Website eingeschränkt sein.<br>
                      <br>
                      <strong>Google Maps</strong><br>
                      Diese Webseite verwendet das Produkt Google Maps von Google Inc. Durch Nutzung dieser Webseite erklären sie sich mit der Erfassung, Bearbeitung sowie Nutzung der automatisiert erhobenen Daten durch Google Inc., deren Vertreter sowie Dritter einverstanden. Die Nutzungsbedingungen von Google Maps finden sie hier<br>
                      <br>
                      <strong>Zwecke der Datenverarbeitung</strong><br>
                      Wir werden Ihre personenbezogenen Daten zu folgenden Zwecken verarbeiten:<br>
                      <ul style="margin: 12px 0; padding-left: 24px;">
                        <li>um Ihnen diese Website zur Verfügung zu stellen und um diese Website weiter zu verbessern und zu entwickeln;</li>
                        <li>um Nutzungsstatistiken erstellen zu können;</li>
                        <li>um Angriffe auf unsere Website erkennen, verhindern und untersuchen zu können;</li>
                        <li>um auf Ihre Anfragen zu antworten.</li>
                      </ul>
                      <br>
                      <strong>Rechtsgrundlagen der Verarbeitung</strong><br>
                      Wenn Sie eine Beratungsanfrage stellen oder auf anderem Weg mit uns in Kontakt treten um nähere Informationen zu unseren Produkten oder ein Vertragsangebot einzuholen, ist die rechtliche Grundlage für die Verarbeitung Ihrer personenbezogenen Daten die Durchführung vorvertraglicher Maßnahmen sowie die Vertragserfüllung (gemäß Art 6 Abs 1 lit b EU Datenschutz-Grundverordnung). Soweit sonstige Informationen betroffen sind, die Sie selbst zur Verfügung stellen, beruht die Verarbeitung Ihrer personenbezogenen Daten auf Ihrer Einwilligung (gemäß Art 6 Abs 1 lit a EU Datenschutz-Grundverordnung). Im Übrigen ist die rechtliche Grundlage für die Verarbeitung Ihrer personenbezogenen Daten unser überwiegendes berechtigtes Interesse (gemäß Art 6 Abs 1 lit f EU Datenschutz-Grundverordnung), welches darin besteht, die oben genannten Zwecke zu erreichen.<br>
                      <br>
                      <strong>Übermittlung Ihrer personenbezogenen Daten</strong><br>
                      Zu den oben genannten Zwecken werden wir Ihre personenbezogenen Daten an folgende Empfänger übermitteln:<br>
                      <ul style="margin: 12px 0; padding-left: 24px;">
                        <li>von uns eingesetzte IT-Dienstleister;</li>
                        <li>im Falle eines Vertragsschlusses zusätzlich: Montage-, Service- und Kranunternehmen, Zustellfirmen wie Speditionen etc. und unsere Lieferanten;</li>
                      </ul>
                      <br>
                      <strong>Dauer der Speicherung</strong><br>
                      Bei Vertragsanbahnung bzw. Vertragsschluss werden Ihre Daten jedenfalls so lange gespeichert, wie gesetzliche Aufbewahrungspflichten dies erfordern oder potentielle Rechtsansprüche noch nicht verjährt sind. In anderen Fällen, in denen Sie selbst Informationen zur Verfügung stellen, werden wir Ihre Daten so lange speichern, bis Sie Ihre Einwilligung in die Datenverwendung widerrufen. Die bei der Verwendung der Website entstehenden Cookie-Daten für Google Doubleclick werden für maximal 90 Tage gespeichert, Daten für Facebook-Retargeting für maximal 6 Monate.<br>
                      <br>
                      <strong>Ihre Rechte im Zusammenhang mit personenbezogenen Daten</strong><br>
                      Sie sind unter anderem berechtigt (nach den gesetzlichen Maßgaben):<br>
                      <ul style="margin: 12px 0; padding-left: 24px;">
                        <li>zu überprüfen, ob und welche personenbezogenen Daten wir über Sie gespeichert haben und Kopien dieser Daten zu erhalten.</li>
                        <li>die Berichtigung, Ergänzung oder das Löschen Ihrer personenbezogenen Daten, die falsch sind oder nicht rechtskonform verarbeitet werden, zu verlangen.</li>
                        <li>von uns zu verlangen, die Verarbeitung Ihrer personenbezogenen Daten einzuschränken.</li>
                        <li>unter bestimmten Umständen der Verarbeitung Ihrer personenbezogenen Daten zu widersprechen oder die für das Verarbeiten zuvor gegebene Einwilligung zu widerrufen.</li>
                        <li>Datenübertragbarkeit zu verlangen.</li>
                        <li>die Identität von Dritten, an welche Ihre personenbezogenen Daten übermittelt werden, zu kennen.</li>
                        <li>bei der zuständigen Behörde Beschwerde zu erheben.</li>
                      </ul>
                      <br>
                      Soweit Informationen betroffen sind, die Sie selbst zur Verfügung stellen (siehe oben) und die Verarbeitung Ihrer personenbezogenen Daten auf Ihrer Einwilligung beruht, können Sie diese Einwilligung jederzeit widerrufen. Durch den Widerruf der Einwilligung wird die Rechtmäßigkeit der aufgrund der Einwilligung bis zum Widerruf erfolgten Datenverarbeitung nicht berührt.<br>
                      <br>
                      <strong>Unsere Kontaktdaten</strong><br>
                      Sollten Sie zu der Verarbeitung Ihrer personenbezogenen Daten Fragen oder Anliegen haben, wenden Sie sich bitte an uns:<br>
                      JOSEF Fenster & Türen<br>
                      Joze Glavac<br>
                      Hauptstraße 32<br>
                      A-6840 Götzis<br>
                      Tel. <a href="tel:+43552352444" class="content-link">+43 (0)5523 52444</a><br>
                      Fax +43 (0)5523 52446<br>
                      Mail: <a href="mailto:office@josef-fenster-tueren.at" class="content-link">office@josef-fenster-tueren.at</a>
                    </p>
                  </div>
                </div>
              </v-expansion-panel-text>
            </v-expansion-panel>
          </v-expansion-panels>
        </v-container>
      </section>
    </v-main>

    <!-- Footer -->
    <SiteFooter />

    <!-- Desktop-only Buttons (visible on large desktop only) -->
    <v-row v-if="showButtons" class="btns desktop-only" align="center" justify="center" no-gutters>
      <v-btn class="menu-btn" :to="'/'">Startseite</v-btn>
      <v-btn class="menu-btn" :to="'/fensterpage'">Fenster</v-btn>
      <v-btn class="menu-btn" :to="'/tuerenpage'">Haustüren</v-btn>
      <v-btn class="menu-btn" href="https://configurator.varialis.net/?bpi=BC27B19A-C106-404F-96C2-60B7AC4C9FD0" target="_blank" rel="noopener">Haustürenkonfigurator</v-btn>
      <v-btn class="menu-btn" :to="'/innentuerenpage'">Innentüren</v-btn>
      <v-btn class="menu-btn highlight">Impressum</v-btn>
    </v-row>
  </v-app>
</template>

<script setup>
import { ref, onMounted, onUnmounted, nextTick } from 'vue'
import { useRoute, useRouter } from 'vue-router'
import SiteFooter from '@/components/SiteFooter.vue'
import logo from '@/assets/logo.png'

const route = useRoute()
const router = useRouter()
const showButtons = ref(true)
const menuOpen = ref(false)

const navItems = [
  { label: 'Startseite' },
  { label: 'Fenster' },
  { label: 'Haustüren' },
  { label: 'Haustürenkonfigurator' },
  { label: 'Innentüren' },
  { label: 'Impressum' },
]

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
  showButtons.value = window.scrollY < 80
}

onMounted(() => {
  handleScroll()
  window.addEventListener('scroll', handleScroll, { passive: true })
  
  // Scroll to anchor if hash is present in URL
  if (route.hash) {
    nextTick(() => {
      const element = document.querySelector(route.hash)
      if (element) {
        element.scrollIntoView({ behavior: 'smooth', block: 'start' })
      }
    })
  }
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
/* Smooth scrolling for anchor links */
:deep(html) {
  scroll-behavior: smooth;
}

/* Sections */
.section {
  padding: 60px 0;
  transition: padding 180ms ease;
  scroll-margin-top: 80px;
}

.section:first-child {
  padding-top: 80px;
}

.section--light {
  background: #fff;
}

.section--alt {
  background: #f5f5f7;
}

.section-container {
  max-width: 1200px;
  margin: 0 auto;
}

.impressum-content {
  width: 100%;
}

.section-title {
  font-size: 32px;
  font-weight: 700;
  margin: 0 0 32px;
  color: #1d1d1f;
  letter-spacing: -0.01em;
  text-transform: uppercase;
}

.content-block {
  color: #1d1d1f;
}

.content-text {
  font-size: 17px;
  line-height: 1.64706;
  margin: 0 0 24px;
  color: #1d1d1f;
}

.content-text:last-child {
  margin-bottom: 0;
}

.content-link {
  color: #d63031;
  text-decoration: none;
  transition: opacity 0.2s ease;
}

.content-link:hover {
  opacity: 0.8;
  text-decoration: underline;
}

/* Contact Info */
.contact-info {
  padding-right: 32px;
}

.map-container {
  padding-left: 32px;
}

.map-wrapper {
  margin-top: 8px;
}

.map-iframe {
  width: 100%;
  height: 280px;
  border: 0;
  border-radius: 12px;
  overflow: hidden;
}

.map-link {
  margin-top: 8px;
  font-size: 14px;
}

/* Program List */
.program-list {
  margin-top: 16px;
}

.program-items {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.program-items li {
  font-size: 17px;
  line-height: 1.64706;
  color: #1d1d1f;
  padding-left: 24px;
  position: relative;
}

.program-items li::before {
  content: "•";
  position: absolute;
  left: 0;
  color: #d63031;
  font-weight: bold;
}

/* Legal Panels (Accordion) */
.legal-panels {
  max-width: 100%;
  margin: 0 auto;
}

.legal-panels :deep(.v-expansion-panel-title) {
  font-size: 18px;
  font-weight: 600;
  color: #1d1d1f;
  padding: 20px 24px;
}

.legal-panels :deep(.v-expansion-panel-text__wrapper) {
  padding: 24px;
  color: #1d1d1f !important;
}

.legal-panels :deep(.v-expansion-panel-text__wrapper .content-text) {
  color: #1d1d1f !important;
  font-size: 17px !important;
  line-height: 1.64706 !important;
}

.legal-panels :deep(.v-expansion-panel-text__wrapper .content-text p) {
  color: #1d1d1f !important;
  font-size: 17px !important;
  line-height: 1.64706 !important;
  margin: 0 0 16px !important;
}

.legal-panels :deep(.v-expansion-panel-text__wrapper ul) {
  color: #1d1d1f !important;
  margin: 12px 0 !important;
  padding-left: 24px !important;
}

.legal-panels :deep(.v-expansion-panel-text__wrapper li) {
  color: #1d1d1f !important;
  font-size: 17px !important;
  line-height: 1.64706 !important;
  margin-bottom: 8px !important;
}

.legal-panels :deep(.v-expansion-panel-text__wrapper strong) {
  color: #1d1d1f !important;
  font-weight: 700;
}

.legal-panels :deep(.v-expansion-panel) {
  margin-bottom: 8px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  background-color: #ffffff !important;
}

.legal-panels :deep(.v-expansion-panel-title) {
  background-color: #ffffff !important;
}

.legal-panels :deep(.v-expansion-panel:last-child) {
  margin-bottom: 0;
}

/* Header Styles */
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
  max-height: 64px;
}

.spacer { flex: 1; }

.nav-mobile-trigger { display: inline-flex; }

/* Hide hamburger menu on large screens (desktop) */
@media (min-width: 1280px) {
  .nav-mobile-trigger { display: none !important; }
  .responsive-header { display: none !important; }
}

/* Desktop-only buttons */
@media (max-width: 1279.98px) {
  .desktop-only {
    display: none !important;
  }
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
  color: #d63031 !important;
  font-weight: 700 !important;
  text-transform: uppercase !important;
  font-size: 14px !important;
  box-shadow: none !important;
  transition: opacity 0.3s ease;
}

.menu-btn:hover {
  opacity: 0.8 !important;
  background: transparent;
}

.highlight {
  color: #d63031 !important;
}

/* Responsive tweaks */
@media (max-width: 959.98px) {
  .section {
    padding: 60px 0;
  }

  .section-title {
    font-size: 28px;
  }

  .content-text {
    font-size: 16px;
  }

  .contact-info {
    padding-right: 0;
    margin-bottom: 32px;
  }

  .map-container {
    padding-left: 0;
  }

  .legal-panels :deep(.v-expansion-panel-title) {
    font-size: 16px;
    padding: 16px 20px;
  }

  .legal-panels :deep(.v-expansion-panel-text__wrapper) {
    padding: 20px;
  }
}

@media (min-width: 1280px) {
  .section-title {
    font-size: 36px;
  }
}
</style>
