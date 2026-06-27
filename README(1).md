# Pastel Motion & Presence Card

Custom Lovelace card per Home Assistant per il monitoraggio di sensori di
movimento/presenza, in stile pastello coerente con le altre card Pastel
della stessa dashboard.

## Funzionalità

- Box riepilogo con illustrazione SVG e conteggio "X/Y attivi" + barra di
  progresso.
- Righe sensore cliccabili: il tap apre il popup "more-info" nativo di Home
  Assistant (stato attuale + grafico storico).
- **Differenza rispetto alle altre card Pastel "di sicurezza"**: qui lo
  stato "Rilevato" usa il colore di base scelto nell'editor, e NON un rosso
  fisso — il movimento/presenza è considerato informativo, non un allarme.
- Colore di base della card personalizzabile (8 tonalità pastello) tramite
  editor visuale.

## Installazione

### Tramite HACS
1. HACS → Frontend → menu (⋮) → **Repository personalizzati**
2. Aggiungi l'URL del repository GitHub, categoria "Lovelace"
3. Cerca "Pastel Motion & Presence Card" e installala

### Manuale
1. Copia `pastel-motion-presence-card.js` in `config/www/`
2. Aggiungi la risorsa in **Impostazioni → Dashboard → Risorse**:
   - URL: `/local/pastel-motion-presence-card.js`
   - Tipo: **JavaScript Module** (obbligatorio: il file usa `import`
     dinamici a livello principale)

## Configurazione (YAML)

```yaml
type: custom:pastel-motion-presence-card
title: Movimento e Presenza
subtitle: Piano terra
icon: mdi:motion-sensor
color: amber
show_progress_bar: true
entities:
  - entity: binary_sensor.presenza_bagno_pt
    name: Presenza Bagno Pt.
  - binary_sensor.presenza_ufficio
  - binary_sensor.base_scala
```

Puoi anche configurarla interamente dall'editor visuale dalla dashboard.

### Colori disponibili
`amber` · `blue` · `green` · `pink` · `purple` · `red` · `teal` · `orange`

## Note tecniche

- Compatibile con qualsiasi `binary_sensor` con stato `on`/`off`
  (tipicamente `device_class: motion` o `occupancy`).
- Carica `lit-element`/`lit-html` da CDN per stabilità nel tempo.
