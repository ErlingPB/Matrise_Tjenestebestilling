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



# Beslutningslogikk

Dette dokumentet beskriver beslutningslogikken i POC-en.

## 1. Første vurdering

Saksbehandler starter med tre valg:

| Valg | Hva betyr det? | Videre flyt |
|---|---|---|
| Ikke bestill nå | Leverandør tilfører ikke nok verdi nå | Gå direkte til saksnotat |
| Hent mer info | Grunnlaget er for svakt | Gå direkte til saksnotat |
| Bestill tjeneste | Leverandør kan tilføre verdi | Vurder kostnad og retning |

## 2. Kostnadsestimat

Når saksbehandler velger «Bestill tjeneste», må saksbehandler anslå skadekostnad.

| Estimat | Foreløpig veiledning |
|---|---|
| Under 10 000 | Vurder kontantoppgjør, digital vurdering eller mer informasjon fra kunden |
| 10 000–50 000 | Små skader bør ofte løses uten fysisk tjeneste hvis saken er enkel |
| 50 000–100 000 | Takst er ikke alltid nødvendig, men kan være nyttig i enkelte saker |
| Over 100 000 | Takst bør normalt vurdere omfang, årsak og videre håndtering |

## 3. Foreløpig retning

Saksbehandler velger hva saken foreløpig peker mot.

| Retning | Veiledning |
|---|---|
| Mulig avslag | Vurder om dokumentasjonen er god nok. Takst kan være nyttig hvis vi må dokumentere avslaget |
| Kontantoppgjør | Vurder om mer informasjon fra kunden er nok til å løse saken uten tjeneste |
| Reparasjon | Gå videre hvis leverandør skal vurdere, begrense eller reparere skaden |

## 4. Når appen stopper før matrisen

Appen sender saken direkte til oppsummering når den foreløpige vurderingen tilsier at saken kan løses uten tjeneste.

I denne versjonen gjelder dette særlig:

- under 10 000
- 10 000–50 000
- 50 000–100 000 kombinert med kontantoppgjør

Dette er bevisst konservativt. Formålet er å hindre unødvendige leverandørbestillinger.

## 5. Når appen sender saken videre til matrisen

Appen sender saken videre til hendelsesmatrisen når saken trolig trenger leverandørvurdering.

Eksempler:

- 50 000–100 000 og mulig avslag
- 50 000–100 000 og reparasjon
- over 100 000

## 6. Hendelsesmatrise

Når saken går videre til matrisen, velger saksbehandler:

1. hendelse
2. årsak/kilde

Appen returnerer tjeneste fra `serviceMatrix`.

Eksempler:

| Hendelse | Årsak/kilde | Tjeneste |
|---|---|---|
| Akutt behov for hjelp | Alle hendelser | 08. Førstehjelp |
| Vannskade | Vannledning Innvendig Åpen/Skjult | 07. Håndverk |
| Andre Bygningsskader | Glass | 03. Glassmester |

## 7. Saksnotat

Til slutt lager appen et saksnotat basert på valgene.

Saksnotatet er ment som et utgangspunkt, ikke en fasit.
