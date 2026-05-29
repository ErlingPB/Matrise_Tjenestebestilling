# Teknisk oversikt

## Arkitektur

Appen er en statisk enkeltside-app i én HTML-fil.

```text
index.html
├── HTML-struktur
├── CSS-design
└── JavaScript-logikk
```

## Viktige JavaScript-deler

| Del | Funksjon |
|---|---|
| `serviceMatrix` | Inneholder hendelser, årsaker og anbefalt tjeneste |
| `state` | Holder brukerens valg gjennom flyten |
| `evaluateInitialChoice()` | Styrer første beslutning og om saken skal videre |
| `getPreAssessmentPath()` | Bestemmer om saken stopper eller går til matrisen |
| `showRecommendation()` | Slår opp anbefalt tjeneste etter hendelse og årsak |
| `buildCaseNote()` | Lager forslag til saksnotat |
| `toggleTheme()` | Bytter mellom lys og mørk modus |

## LocalStorage

Appen bruker LocalStorage til å huske valgt tema:

```javascript
localStorage.setItem("leverandor-theme", next);
```

Dette påvirker bare visningen. Det lagrer ikke saksdata.

## Personvern og data

Denne POC-en sender ikke data til en server.

Alle valg ligger bare i nettleseren mens siden er åpen.

## Anbefalt videre teknisk struktur

Hvis appen skal videreutvikles, kan filene deles slik:

```text
src/
├── index.html
├── styles.css
├── app.js
└── service-matrix.json
```

Fordeler:

- enklere vedlikehold
- enklere kodegjennomgang
- enklere testing av matrisen
- mulig å oppdatere matrisen uten å endre hele appen

## Kjente begrensninger i POC

- Ingen brukerinnlogging
- Ingen logging av valg
- Ingen integrasjon mot NICE eller In4mo
- Ingen sentral versjonsstyring av matrisen
- Saksnotat må kopieres manuelt
- Alle regler ligger hardkodet i JavaScript
