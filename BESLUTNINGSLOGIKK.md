# Testcases

Bruk disse testene etter endringer i koden.

## Test 1: Ikke bestill

1. Velg «Ikke bestill nå».
2. Trykk «Gå videre».
3. Forventet resultat:
   - appen går til steg 3
   - saksnotat sier at tjeneste ikke bestilles
   - «Tilbake» går til steg 1

## Test 2: Hent mer informasjon

1. Velg «Hent mer info».
2. Trykk «Gå videre».
3. Forventet resultat:
   - appen går til steg 3
   - saksnotat sier at mer informasjon må hentes
   - «Tilbake» går til steg 1

## Test 3: Bestill tjeneste, liten kontantsak

1. Velg «Bestill tjeneste».
2. Velg «Under 10 000».
3. Velg «Kontantoppgjør».
4. Trykk «Gå videre».
5. Forventet resultat:
   - appen går til steg 3
   - appen anbefaler vurdering uten tjeneste
   - saksnotat beskriver at saken bør vurderes videre før eventuell bestilling

## Test 4: Bestill tjeneste, stor reparasjon

1. Velg «Bestill tjeneste».
2. Velg «Over 100 000».
3. Velg «Reparasjon».
4. Trykk «Gå videre».
5. Forventet resultat:
   - appen går til steg 2
   - hendelsesmatrisen vises

## Test 5: Akutt behov

1. Gå til steg 2 via en sak som sendes videre.
2. Velg «Akutt behov for hjelp».
3. Velg «Alle hendelser».
4. Forventet resultat:
   - anbefalt tjeneste er `08. Førstehjelp`

## Test 6: Vannskade med håndverk

1. Gå til steg 2.
2. Velg «Vannskade».
3. Velg «Vannledning Innvendig Åpen/Skjult».
4. Forventet resultat:
   - anbefalt tjeneste er `07. Håndverk`

## Test 7: Dark mode og nedtrekksliste

1. Slå på mørk modus.
2. Gå til steg 2.
3. Åpne nedtrekkslisten for årsak/kilde.
4. Forventet resultat:
   - tekst og bakgrunn er lesbare

## Test 8: Tilbakeknapper

1. Test tilbake fra steg 2 til steg 1.
2. Test tilbake fra steg 3 etter en stopp i steg 1.
3. Test tilbake fra steg 3 etter et matriseløp.
4. Forventet resultat:
   - stopp i steg 1 går tilbake til steg 1
   - matriseløp går tilbake til steg 2
