<div align="center">

<img src="rosetta-logo-toolkit.jpg" alt="Rosetta Logo" width="800" style="border-radius: 12px; box-shadow: 0 8px 24px rgba(0,0,0,0.5);" />

# 🏛️ ROSETTA
### *The Universal Decryption & Localization Suite for Visual Novels & Narrative Games*

[![Python Version](https://img.shields.io/badge/Python-3.10%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Engines](https://img.shields.io/badge/Supported%20Engines-Ren'Py%20%7C%20RPG%20Maker%20%7C%20Godot%20%7C%20Unity-orange.svg)]()
[![Pipeline](https://img.shields.io/badge/Pipeline-FORGE%202%20%7C%20Dual--NMT-cyan.svg)]()
[![Architecture](https://img.shields.io/badge/Architecture-Rosetta%20Swarm%203.0-magenta.svg)]()
[![Author](https://img.shields.io/badge/Author-adisc-blueviolet.svg)](https://github.com/adisc99)

**Rosetta** è la suite universale e ad alte prestazioni per l'ispezione, decifrazione, traduzione neurale e localizzazione automatica di **Visual Novel e giochi a forte componente narrativa**.
</div>

---

## 🌟 Perché "Rosetta"?

Ispirato alla leggendaria *Stele di Rosetta*, il software funge da **chiave universale** per decodificare gli script di Visual Novel e giochi narrativi, abbattendo ogni barriera linguistica. 

Unisce in un unico **Master Hub Orchestrator (`rosetta.py`)** e nella suite grafica unificata **Rosetta Studio 2026** il supporto completo a 4 motori di gioco leader, preservando il codice originale, le formattazioni visive, i tag dei dialoghi e la coerenza narrativa:

```
                                 🏛️ ROSETTA (Master Hub & Studio)
               ┌─────────────────────┬─────────────────────┬─────────────────────┐
               ▼                     ▼                     ▼                     ▼
        📜 Ren'Py (RITT)      ⚔️ RPG Maker (RPGMT)    🤖 Godot (GITT)       🎮 Unity (UITT)
        .rpa / .rpy / .rpyc   MV / MZ data/*.json   .pck / project.godot   *_Data / .assets
```

---

## 🎮 Matrice dei Motori Supportati

| Modulo | Motore di Gioco | Formati & Strutture Supportate | Caratteristiche Principali |
| :--- | :--- | :--- | :--- |
| **`rosetta renpy`** | **Ren'Py Engine** *(Visual Novels)* | `.rpa`, `.rpy`, `.rpyc`, `game/tl/` | Decompressione RPA, estrazione dialoghi e menu, isolamento `characters.rpy`, mod patch F8, esportazione Android APK. |
| **`rosetta rpgm`** | **RPG Maker MV / MZ / RGSS** | `data/*.json`, `System.json`, `Map*.json`, `locales/` (DKTools) | Parsing chirurgico dialoghi ed eventi, protezione codici di controllo `\C`, `\N`, `\V`, iniezione in-place e backup deterministico. |
| **`rosetta godot`** | **Godot Engine 3 & 4** | `.pck`, `.tscn`, `.gd`, pacchetti binari | Decompilatore nativo `.pck`, discovery automatica chiavi AES-256 via analisi statica o memory auto-dump (RAM Livello 3), generazione CSV e repack standalone. |
| **`rosetta unity`** | **Unity Engine** *(Mono & IL2CPP)* | `*_Data/`, `resources.assets`, asset bundles | Deployment automatico runtime BepInEx XUnity AutoTranslator, parsing TypeTree/TextMeshPro e iniezione chirurgica offline. |

---

## ✨ Caratteristiche Fondamentali

1. **Auto-Detection Intelligente**:
   Basta passare il percorso di una cartella di gioco o di un archivio: Rosetta rileva automaticamente il motore (*Ren'Py, RPG Maker, Godot o Unity*) e orchestra la pipeline appropriata.
2. **FORGE 2 Pipeline & Rosetta Swarm 3.0**:
   - **Dual-NMT Pipeline**: Combinazione ad altissima velocità tra modelli neurali specializzati (DeepL, Google NMT, Marian MT) e validazione sintattica.
   - **Rosetta Swarm 3.0**: Dispatching concorrente multi-thread con gestione dinamica delle code di traduzione, watchdog auto-save e zero tempi morti.
   - **SQLite WAL Persistent Cache**: Ogni frase tradotta viene indicizzata e salvata in un database SQLite con Write-Ahead Logging per azzerare i costi e le chiamate duplicate tra aggiornamenti di gioco.
3. **Preservazione Rigorosa di Tag & Variabili**:
   Protegge tag grafici (`{b}`, `{i}`, `{color=...}`, `\n`, `\C[2]`, `\N[1]`) e placeholder di codice (`[player_name]`, `%(var)s`) impedendo qualsiasi corruzione o crash in-game.
4. **Ripristino Deterministico (`rosetta restore`)**:
   Snapshot preventivi e manifest automatici garantiscono il rollback istantaneo del gioco allo stato originale incontaminato con un solo clic.
5. **Smart Asset Compression**:
   Algoritmo di ottimizzazione e ricompressione integrato per ridurre le dimensioni dei giochi fino al 60-80% senza perdita di qualità, facilitando la distribuzione.
6. **Zero Spyware & Massima Privacy**:
   Nessun dato inviato a server terzi, zero telemetria invasiva, massima trasparenza etica.

---

## 🖥️ Interfaccia Utente

Rosetta offre due modalità di interazione:

### 1. Rosetta Studio 2026 (Suite Grafica Unificata)
La dashboard moderna e fluida sviluppata in Flutter/Flet:
- Dashboard unificata con drag & drop folder scanner.
- Workspace dedicati per ogni motore (Ren'Py, RPG Maker, Godot, Unity).
- Telemetria live, cache monitor e gestione chiavi di crittografia.
- Supporto a tema Dark Obsidian e Light.

```bash
python3 rosetta_studio.py       # Oppure rosetta.exe / RosettaStudio.exe
```

### 2. Master CLI (`rosetta.py`)
Per utenti avanzati, automazioni, script e server headless:
```bash
python3 rosetta.py --help
```

---

## 📦 Installazione

### 1. Clonazione del Repository
```bash
git clone https://github.com/adisc99/RITT.git rosetta
cd rosetta
```

### 2. Installazione Dipendenze
```bash
pip install -r requirements.txt
```

*(Opzionale)* Per abilitare il comando globale `rosetta` nel terminale di sistema:
```bash
pip install -e .
```

---

## ⚙️ Configurazione Chiavi API (`.env`)

Crea o modifica il file `.env` nella directory principale (il template è disponibile in `.env.example`):

```env
# Google Gemini API
GEMINI_API_KEY="AIzaSy..."
GEMINI_MODEL="gemini-2.5-flash"
LLM_PROVIDER="gemini"

# DeepL API Key (Opzionale)
DEEPL_API_KEY=""

# OpenAI / Anthropic / Groq (Opzionali)
OPENAI_API_KEY=""
ANTHROPIC_API_KEY=""
GROQ_API_KEY=""
```

---

## 🚀 Utilizzo Rapido da Riga di Comando (CLI)

### 🩺 1. Verifica Salute di Sistema (`doctor`)
Controlla la configurazione dell'ambiente, le API Key caricate e lo stato della memoria cache:
```bash
python3 rosetta.py doctor
```

### 🔍 2. Scansione Statistica del Gioco (`scan`)
Analizza archivi e script, calcola frasi e parole e salva il manifest locale `.rosetta_scan.json`:
```bash
# Auto-detection automatica:
python3 rosetta.py scan /percorso/del/gioco

# Specificando il motore esplicito:
python3 rosetta.py renpy scan /percorso/gioco_renpy
python3 rosetta.py rpgm scan /percorso/gioco_rpgm
python3 rosetta.py godot scan /percorso/gioco_godot
python3 rosetta.py unity scan /percorso/gioco_unity
```

### 🌐 3. Traduzione Neurale (`translate`)
```bash
# Traduzione automatica con iniezione diretta:
python3 rosetta.py translate /percorso/del/gioco --auto-inject

# Con motore neurale Google Translate gratuito:
python3 rosetta.py translate /percorso/del/gioco --engine google
```

### 🔑 4. Recupero Chiavi AES Godot (`dump-key`)
Estrae automaticamente la chiave AES-256 da binari Godot protetti tramite analisi statica o auto-dump RAM:
```bash
python3 rosetta.py dump-key /percorso/del/gioco
```

### 🗜️ 5. Compressione Asset (`compress`)
Ottimizza e riduce il peso del gioco:
```bash
python3 rosetta.py compress /percorso/del/gioco --pack-zip
```

### 🛡️ 6. Ripristino Backup (`restore`)
Ripristina istantaneamente il gioco originale eliminando i file modificati:
```bash
python3 rosetta.py restore /percorso/del/gioco
```

---

## 📁 Struttura del Progetto

```
rosetta/
├── rosetta.py                      # 🏛️ Master Hub & CLI Universale (Auto-Detector)
├── rosetta_studio.py               # 🌟 Rosetta Studio 2026 (Suite Grafica Flet/Flutter)
├── rosetta-logo-toolkit.jpg        # 🎨 Logo ufficiale di Rosetta Suite
├── build_portable.py               # 📦 Builder standalone per release portabili Windows
├── renpytranslator/                # 📜 Modulo Ren'Py (Parser RPA/RPYC, TL generator, Mobile Bridge)
├── rpgmtranslator/                 # ⚔️ Modulo RPG Maker MV/MZ (JSON parser, code protections)
├── godottranslator/                # 🤖 Modulo Godot Engine (PCK builder, AES crypto, dump RAM)
├── unitytranslator/                # 🎮 Modulo Unity Engine (Asset extractor, BepInEx AutoTranslator)
├── rosetta_ui/                     # 🎨 Componenti e visuali di Rosetta Studio 2026
├── data/                           # 💾 Template, font cyberpunk, configurazioni e icone
└── docs/                           # 📚 Guide e documentazione tecnica
```

---

## 🧪 Esecuzione dei Test Automatizzati

Rosetta include una suite di test unitari che coprono de-compilatori, parser di script, preservazione tag, estrazione archivi binari e gestione backup:

```bash
python3 -m unittest discover tests
```

---

## 📄 Licenza e Crediti

* **Autore / Ideatore**: `adisc`
* **Licenza**: MIT License
* **Repository Release**: [github.com/adisc99/rosetta](https://github.com/adisc99/rosetta)
* **Special Thanks**: *Giobol The Librarian* & la Comunità Traduttori Italiani Visual Novel.
