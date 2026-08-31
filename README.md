# Leanhuset — interaktiv nettside for PRO-2804

Én enkelt fil, `index.html`, uten eksterne avhengigheter. Kan legges rett i et GitHub-repo og publiseres som GitHub Pages.

## Hvordan den virker

Rammen i huset (Mål, Just-in-Time, Jidoka, Involvering, Standardisering, Stabilitet) står fra første uke, slik som i bokas figur 2.4 [1]. De enkelte aktivitetsfeltene dukker opp uke for uke og fyller huset mot figur 2.5.

- **Ukeslider** (34–46) styrer hvor mye som er avdekket.
- **Faglærervisning** viser kommende felt i grått, slik at du kan se hele oppbyggingen.
- Hvert felt og hver husdel er klikkbar og fører til en underside med egen URL (`#/femS`, `#/jidoka` osv.), som kan lenkes direkte fra Canvas.
- Felt merket `*` er tillegg i PRO-2804 og står ikke i Dennis' figur 2.5 (PDCA og visuell ledelse).

## Vedlikehold

All redigering skjer i `index.html`, i to lister nederst i fila.

### Flytte når et felt dukker opp

Finn elementet i lista `ELEMENTER` og endre `uke`:

```js
{id:'tpm', navn:'TPM', uke:37, i:['inv','stab'],
 kort:'Totalt produktivt vedlikehold — maskinens stabilitet er operatørens ansvar.'},
```

`i:[...]` er hvilke deler av huset feltet står i. Gyldige verdier: `mal`, `jit`, `inv`, `jidoka`, `std`, `stab`. Et felt kan stå flere steder — det er slik figur 2.5 faktisk er bygd.

### Skrive innholdet på en underside

Legg inn en nøkkel i objektet `INNHOLD` med samme `id` som elementet:

```js
tpm:{ref:['dennis','liker'], html:`
<p>Brødtekst i HTML …</p>
<h3>Mellomtittel</h3>
<div class="callout"><b>Poeng som skal sitte.</b> …</div>
`},
```

Felt uten innhold får automatisk en «ikke skrevet ennå»-side, så siden virker uansett.

Gyldige kildenøkler i `ref`: `dennis`, `ohno`, `sobek`, `deming`, `hirano`, `liker`, `rother`. Nummereringen settes automatisk. Nye kilder legges inn i objektet `R`.

### Nyttige klasser i brødteksten

| Klasse | Bruk |
|---|---|
| `<div class="callout">` | Framhevet poeng, farget etter husdelen |
| `<table>` | Vanlig tabell, ferdig stilsatt |
| `<h3>` | Mellomtittel |

## Publisering

Fila er selvstendig. Last den opp i repoets rot og slå på GitHub Pages fra `main`-branchen, rotmappa. Endringer publiseres ved å laste opp en ny versjon av `index.html`.

## Kilder

[1] P. Dennis, *Lean Production Simplified: A Plain-Language Guide to the World's Most Powerful Production System*, 3. utg. Boca Raton, FL, USA: CRC Press, 2016, fig. 2.4–2.5.
