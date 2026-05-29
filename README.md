Fremtind veileder for leverandørtjenester
Interaktiv POC for beslutningsstøtte ved bestilling av leverandørtjenester fra NICE/In4mo.
Løsningen hjelper saksbehandler med å vurdere:
om vi skal bestille leverandørtjeneste
om vi bør hente mer informasjon først
om saken heller bør løses uten tjeneste, for eksempel med kontantoppgjør
hvilken hendelse og årsak/kilde som peker mot riktig tjeneste i In4mo
hvilket saksnotat som kan dokumentere vurderingen
Dette er en statisk HTML-app. Den krever ingen backend, database eller byggesteg.
---
Innhold i pakken
```text
fremtind-github-pakke/
├── index.html
├── README.md
├── docs/
│   ├── BESLUTNINGSLOGIKK.md
│   ├── TEKNISK_OVERSIKT.md
│   └── TESTCASES.md
├── .gitignore
└── LICENSE.md
```
---
Kom raskt i gang
Last ned eller klon repoet.
Åpne `index.html` direkte i nettleseren.
Test flyten:
Velg om tjeneste skal bestilles.
Velg kostnadsestimat og foreløpig retning hvis du velger «Bestill tjeneste».
Velg hendelse og årsak/kilde hvis appen sender deg videre til matrisen.
Kopier saksnotatet i siste steg.
Ingen installasjon er nødvendig.
---
Formålet med POC-en
Målet er å gjøre det enklere for saksbehandler å ta en likere og bedre begrunnet beslutning før bestilling av leverandørtjeneste.
Appen skal støtte, ikke erstatte, faglig vurdering.
Den viktigste beslutningen er ikke hvilken tjeneste som skal bestilles. Den viktigste beslutningen er om vi skal bestille tjeneste i det hele tatt.
---
Hovedflyt
Steg 1: Vurder behov
Saksbehandler velger ett av tre hovedvalg:
Ikke bestill nå
Hent mer info
Bestill tjeneste
Hvis saksbehandler velger «Bestill tjeneste», ber appen også om:
estimert skadekostnad
foreløpig retning i saken
Dette gir en tidlig vurdering av om saken bør løses uten tjeneste eller gå videre til matrisen.
Steg 2: Velg hendelse
Hvis saken skal videre, velger saksbehandler:
hendelse
årsak/kilde
Appen slår opp riktig tjeneste i `serviceMatrix` i JavaScript-koden.
Steg 3: Dokumenter vurderingen
Appen lager et forslag til saksnotat som kan kopieres og tilpasses.
---
Beslutningsprinsipper
POC-en bygger på disse prinsippene:
Bestill bare når leverandør tilfører verdi.
Små og enkle saker bør ofte løses uten fysisk tjeneste.
Ved mulig avslag bør vi vurdere om dokumentasjonen er god nok.
Ved kontantoppgjør bør vi vurdere om mer informasjon fra kunden er nok.
Ved høyere skadekostnad bør takst oftere vurdere omfang, årsak og videre håndtering.
Akutt behov for hjelp er egen hendelse og leder til `08. Førstehjelp`.
---
Bestillingsmatrise
Matrisen ligger i `serviceMatrix` i `index.html`.
Eksempel:
```javascript
"Vannskade": {
  icon: "💧",
  short: "Vann, rør, avløp og våtrom",
  causes: [
    { cause: "Vannledning Innvendig Åpen/Skjult", service: "07. Håndverk" }
  ]
}
```
Når matrisen endres, er det primært `serviceMatrix` som må oppdateres.
---
Klarspråk
Tekstene i POC-en er skrevet med disse prinsippene:
viktigste først
korte setninger
aktive formuleringer
tydelige valg
minst mulig stammespråk
direkte språk til saksbehandler
Eksempel:
```text
Ikke bestill ennå. Avklar årsak, omfang, bilder, dokumentasjon, dekning eller behov for leverandør først.
```
---
Teknologi
HTML
CSS
JavaScript
LocalStorage for valgt lys/mørk modus
Ingen eksterne biblioteker
Ingen backend
---
Videre utvikling
Mulige neste steg:
Splitte HTML, CSS og JavaScript i egne filer.
Legge `serviceMatrix` i en egen JSON-fil.
Legge inn testsaker nederst i appen.
Logge valg anonymt for å se hvordan veilederen brukes.
Lage PowerApps- eller Teams-integrasjon.
Koble appen til offisiell og versjonsstyrt matrise.
---
Status
Dette er en POC og skal kvalitetssikres faglig før eventuell produksjonssetting.
