# Prison Cells & Rankup (Skript) – 1.21

> Et simpelt Prison Cells- og Rankup-system til Minecraft 1.21, lavet i **Skript**. Spillere kan købe/sælge celler og ranke op via GUI.

---
## Sådan bruger du dokumentationen

**1. Brug indholdsfortegnelsen:** Klik på et punkt for at hoppe direkte til den relevante sektion.

**2. Se eksempler og kommandoer:** Alle vigtige kommandoer og eksempler er fremhævet i kodeblokke eller punktopstillinger.

**3. Læs “Data & Fejlfinding” hvis du oplever problemer:** Her finder du typiske fejl og løsninger.

**4. Brug “Forslag til Udvidelser” for inspiration:** Hvis du vil bygge videre på systemet.

---
## Indhold

- [Introduktion](#introduktion)
- [Krav](#krav)
- [Installation](#installation)
- [Opsætning](#opsætning)
- [Brug (Spiller)](#brug-spiller)
- [Filstruktur](#filstruktur)
- [Data & Fejlfinding](#data--fejlfinding)
- [Forslag til Udvidelser](#forslag-til-udvidelser)
- [License](#license)

---
# Prison Cells (Skript) – 1.21

Et simpelt “Prison Cells”-system lavet i **Skript**, hvor spillere kan:
- Åbne en **GUI** ved at højreklikke på et skilt
- **Købe** en celle (1 celle pr. spiller)
- **Sælge** sin celle tilbage via kommando

> Scriptet håndterer kun **ejerskab + køb/salg**. Hvis celler skal være “låste” (kun ejeren kan bygge), anbefales WorldGuard (ikke inkluderet i denne version).

---

## Krav


# Prison Cells & Rankup (Skript) – 1.21

- **skVault** (enten som `.sk` script eller addon der giver balance/withdraw)

## Introduktion

**Prison Cells**: Spillere kan købe én celle via GUI (åbnes fra skilt), sælge den igen, og admins kan oprette/fjerne celler. Ejerskab og økonomi håndteres automatisk.

**Rankup**: Spillere kan ranke op via en menu, hvor pris og næste rank vises. Understøtter Vault og LuckPerms.

---

## Krav

- Minecraft **1.21** (Paper/Spigot)
- **Skript** (nyeste version til 1.21)
- **Vault**
- **Economy-plugin** (fx EssentialsX Economy)
- **LuckPerms** (til rankup)
- **skVault** (til economy-funktioner i Skript)
- Valgfrit: **skript-yaml** eller **SkBee** (for YAML-support)

---

## Installation

1. Læg `.sk`-filerne i `plugins/Skript/scripts/`
2. Læg evt. `cells.yml` i en `yaml/`-mappe hvis du bruger YAML-support
3. Reload Skript: `/sk reload prison_cells` og `/sk reload rankup`

---

## Opsætning

### Opret celler (admin)
- `/celladmin add <id> <pris>`  
   Eksempel: `/celladmin add A1 5000`
- `/celladmin list`  
   Viser alle celler
- `/celladmin remove <id>`  
   Fjerner en celle (og ejerskab hvis relevant)

### Skilt til GUI
Lav et skilt og skriv på **linje 1**: `[Cells]`  
Når en spiller højreklikker, åbnes GUI’en.

### Rankup-menu
- `/rankup` åbner en menu hvor spilleren kan ranke op

---

## Brug (Spiller)

### Celler
- Se din celle: `/cell`
- Sælg din celle: `/cellsell`  
   (Refund % styres i scriptets options)

### Rankup
- Åbn menu: `/rankup`
- Klik for at ranke op (hvis du har penge nok)

---

## Filstruktur

Anbefalet struktur:

```
mcskript/
├── prison_cells.sk
├── rankup.sk
├── README.md
└── yaml/
      └── cells.yml
```

---

## Data & Fejlfinding

### Data (variabler)
- `{cells::*}` – Liste over alle celler (IDs)
- `{cell::<id>::price}` – Pris på cellen
- `{cell::<id>::ownerUUID}` – Ejerens UUID
- `{cell::<id>::ownerName}` – Ejerens navn
- `{playercell::<uuid>}` – Hvilken celle spilleren ejer
- `{cellgui::<uuid>::<slot>}` – Midlertidig mapping til GUI-klik

### Fejlfinding
- Vault economy not found: Tjek at Vault + economy-plugin er installeret og virker (`/balance`)
- GUI åbner ikke fra skilt: Tjek at linje 1 er **præcis** `[Cells]` og at Skript er reloaded uden fejl

### Kendte begrænsninger
- Ingen teleport eller automatisk beskyttelse af celler (brug evt. WorldGuard)
- Ingen pagination i GUI (viser kun første side)

---

## Forslag til Udvidelser

- WorldGuard-integration (automatisk beskyttelse af celler)
- Flere celler pr. spiller (fx rank-baseret)
- Paging i GUI (Next/Prev)
- Bekræftelsesmenu ved køb
- Leje celler (tidsbegrænset)

---

## License

Brug frit på din server. 🙂

Valgfrit (kun hvis du vil læse rankup.yml inde fra Skript):
- **skript-yaml** eller **SkBee** (YAML-support)

## Filplacering
Anbefalet struktur:
