# $$DÓJA — Institutional Art & Finance$$

> L'intersezione tra arte e capitale.

Dashboard dimostrativa per la gestione di un portfolio di opere d'arte, con estetica istituzionale: tema scuro, accento oro, tipografia editoriale e micro-interazioni. Il progetto è interamente statico (HTML, CSS e JavaScript vanilla, nessun build step) e salva i dati nel `localStorage` del browser.

**Demo:** [https://panosettistefano.github.io/DOJA-proget/](https://panosettistefano.github.io/DOJA-proget/)

---

## File del progetto

| File | Descrizione |
|------|-------------|
| `index.html` | Applicazione principale: login, dashboard, portfolio, impostazioni e note legali |
| `landing.html` | Landing page di presentazione (hero, feature, collezione, statistiche, footer) |
| `Doja19.html` | Versione precedente a file singolo, con immagini remote (conservata come riferimento) |
| `img/` | Immagini locali degli asset (Van Gogh, Dalì, Ligabue) e risorse grafiche |

Tutte le pagine sono autonome: nessuna dipendenza locale oltre alle immagini, nessun processo di compilazione.

---

## Funzionalità di `index.html`

### Accesso
- Schermata di login con credenziali demo
- Sessione persistente tramite `localStorage` (`doja_session`)
- Toast di feedback e animazione di errore (shake) in caso di credenziali errate

### Dashboard
- Patrimonio netto totale calcolato dagli asset e dalla liquidità
- Grafico dello storico del patrimonio (Chart.js)
- Log di terminale live generati dinamicamente
- Elenco delle acquisizioni recenti con apertura del dettaglio

### Portfolio
- Griglia completa degli asset con status (`In Vault` / `Exhibited`)
- Modale di dettaglio con immagine, valutazione e descrizione
- Aggiunta manuale di un nuovo asset
- Registrazione di transazioni (deposito / prelievo)
- Eliminazione di un asset

### Impostazioni
- Tema chiaro / scuro
- Lingua interfaccia: Italiano / English
- Valuta visualizzata: Euro / Dollaro
- Export del portfolio in CSV
- Termina sessione

### Esperienza
- Layout responsive con menu mobile
- Cursore personalizzato su desktop
- Transizioni e animazioni curate
- Effetti sonori di interfaccia via Web Audio API
- Tema scuro e chiaro con persistenza della preferenza

---

## Stack tecnico

- **HTML5 / CSS3 / JavaScript (vanilla)** — nessun framework, nessun bundler
- **Tailwind CSS** via CDN con configurazione inline (`darkMode: 'class'`, palette custom)
- **Lucide** per le icone
- **Chart.js** per il grafico del patrimonio
- **Google Fonts** — Plus Jakarta Sans e JetBrains Mono

---

## Avvio in locale

Apri direttamente `index.html` nel browser, oppure servi la cartella con un server statico:

```bash
# Python
python3 -m http.server 8000

# Node (npx)
npx serve .
```

Poi visita `http://localhost:8000/index.html`.

Con VS Code è sufficiente l'estensione **Live Server**: tasto destro su `index.html` → *Open with Live Server*.

---

## Credenziali demo

| Campo | Valore |
|-------|--------|
| Terminal ID | `ADMIN` |
| Security Key | `1234` |

---

## Dati e persistenza

Lo stato dell'applicazione è salvato nel `localStorage` alla chiave `doja_data`; la sessione alla chiave `doja_session`.

Per ripartire da zero, apri la console del browser ed esegui:

```js
localStorage.removeItem('doja_data');
localStorage.removeItem('doja_session');
location.reload();
```

All'avvio, `loadState()` migra automaticamente gli asset di default verso le immagini locali in `img/`, così eventuali salvataggi precedenti che puntano a URL remoti non più validi non rompono la visualizzazione.

---

## Note sul deploy

Il sito è pubblicato tramite **GitHub Pages** dal branch `main`. La cartella `img/` deve essere inclusa nel repository, altrimenti le immagini non saranno disponibili online:

```bash
git add img/
git commit -m "Aggiunge le immagini locali degli asset"
git push
```

---

## Autore

**Stefano Panosetti**

Progetto realizzato a scopo dimostrativo. I dati, le valutazioni e le credenziali sono fittizi.
