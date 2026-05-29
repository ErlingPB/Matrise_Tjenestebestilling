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
