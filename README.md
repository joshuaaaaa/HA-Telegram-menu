# Telegram Menu pro Home Assistant

Komplexní Telegram bot menu pro ovládání a monitoring Home Assistant přes Telegram.

<img width="345" height="414" alt="image" src="https://github.com/user-attachments/assets/83ce6eef-c048-467d-808e-1c5ac6fd4394" />

## 📋 Obsah

- [Funkce](#-funkce)
- [Požadavky](#-požadavky)
- [Instalace](#-instalace)
- [Použití](#-použití)
- [Dostupné příkazy](#-dostupné-příkazy)
- [Struktura menu](#-struktura-menu)
- [Přizpůsobení](#-přizpůsobení)
- [Troubleshooting](#-troubleshooting)

## ✨ Funkce

### Základní přehledy
- 📊 **Stav domácnosti** - teploty, energie, zařízení, osoby
- 🌤 **Počasí** - teplota, vlhkost, tlak ze všech sensorů
- 📡 **Síť** - připojená zařízení, rychlost internetu
- ⚡ **Elektřina** - aktuální spotřeba, napětí, proud, top spotřebiče

### Ovládání a monitoring
- 💡 **Světla** - přehled zapnutých/vypnutých světel s jasem a teplotou
- 🔌 **Switche** - stav všech switchů, doba zapnutí, spotřeba
- 🔥 **Topení** - teploty místností, termostaty, tepelné čerpadlo
- 🔒 **Zabezpečení** - dveře, okna, detektory, alarmy
- 🎵 **Média** - aktivní přehrávače, co hraje, vysavače

### Systémové informace
- 🔋 **Baterie** - přehled všech baterií podle stavu (kritické/střední/dobré)
- 📱 **Systém** - verze HA, uptime, CPU, RAM, disk, počet entit
- ⚠️ **Upozornění** - slabé baterie, otevřená okna, nedostupné entity
- 🆕 **Updaty** - dostupné aktualizace s verzemi

### Pokročilé funkce
- 🎬 **Scény** - seznam všech dostupných scén
- 🤖 **Automatizace** - aktivní/vypnuté automatizace
- 📈 **Statistiky** - spotřeba energie, průměrné teploty, aktivita
- 👥 **Osoby** - kde jsou lidé, GPS pozice, zdroj trackingu
- 📅 **Kalendář** - probíhající události
- 🌅 **Slunce** - východ/západ, elevace, fáze měsíce
- 🗒️ **Notifikace** - aktivní persistent notifications
- 💨 **Kvalita vzduchu** - CO2, vlhkost, AQI

## 📦 Požadavky

### Povinné
- Home Assistant (doporučeno 2024.1+)
- Nakonfigurovaný [Telegram Bot](https://www.home-assistant.io/integrations/telegram_bot/)
- Povolené packages v `configuration.yaml`

### Volitelné (pro plnou funkcionalitu)
- Device tracker integrace (pro sledování osob)
- Speedtest integrace (pro rychlost internetu)
- System Monitor integrace (pro CPU, RAM, disk)
- Calendar integrace (pro události)
- Update entities (pro sledování aktualizací)

## 🚀 Instalace

### 1. Povolení packages

V `configuration.yaml` přidej nebo ověř:

```yaml
homeassistant:
  packages: !include_dir_named packages
```

### 2. Vytvoření adresáře

```bash
mkdir -p /config/packages
```

### 3. Instalace souboru

Ulož `telegram_menu.yaml` do `/config/packages/`

```bash
# Přes SSH nebo File Editor
nano /config/packages/telegram_menu.yaml
# Vlož celý obsah souboru
```

### 4. Kontrola konfigurace

```bash
# Zkontroluj validitu YAML
ha core check
```

### 5. Restart Home Assistant

- **Studio Code Server**: Terminal → `ha core restart`
- **Web UI**: Nastavení → Systém → Restartovat
- **SSH**: `ha core restart`

## 📱 Použití

### Spuštění menu

V Telegramu napiš botovi:

```
/menu
```

Zobrazí se interaktivní menu s tlačítky pro všechny funkce.

### Navigace

- **Klikni na tlačítko** - zobrazí detail vybrané kategorie
- **🔄 Refresh** - aktualizuje data v aktuální kategorii
- **🏠 Menu** - vrátí se do hlavního menu

## 🎮 Dostupné příkazy

### Základní příkazy
| Příkaz | Popis |
|--------|-------|
| `/menu` | Zobrazí hlavní menu |
| `/status` | Rychlý přehled domácnosti |
| `/thp` | Teplota, vlhkost, tlak |
| `/air` | Kvalita vzduchu (CO2, vlhkost, AQI) |
| `/actions` | Menu rychlých akcí |

### Přímé zobrazení (přes menu)
Všechny další funkce jsou dostupné přes interaktivní menu:
- Síť, Elektřina, Světla, Topení
- Zabezpečení, Switche, Baterie, Systém
- Média, Upozornění, Scény, Automatizace
- Updaty, Statistiky, Osoby, Kalendář
- Slunce, Notifikace

## 🗂 Struktura menu

```
🏠 Hlavní menu
├── 📡 Síť - Zařízení doma, rychlost internetu
├── 📊 Stav - Celkový přehled domácnosti
├── ⚡ Elektrika - Spotřeba, napětí, top spotřebiče
├── 🌤 Počasí - THP senzory
├── 💡 Světla - Zapnutá/vypnutá světla
├── 🔥 Topení - Teploty, termostaty, TČ
├── 🔒 Zabezpečení - Dveře, okna, detektory
├── 🔌 Switche - Přehled všech switchů
├── 🔋 Baterie - Stav baterií podle úrovně
├── 📱 Systém - HA verze, CPU, RAM, disk
├── 🎵 Média - Přehrávače, vysavače
├── ⚠️ Upozornění - Varování a problémy
├── 🎬 Scény - Seznam scén
├── 🤖 Automatizace - Aktivní/vypnuté
├── 🆕 Updaty - Dostupné aktualizace
├── 📈 Statistiky - Souhrny spotřeby
├── 👥 Osoby - Kde jsou lidé
├── 📅 Kalendář - Události
├── 🌅 Slunce - Východ/západ, měsíc
└── 🗒️ Notifikace - Aktivní notifikace
```

## 🔧 Přizpůsobení

### Přidání vlastní kategorie

```yaml
automation:
  - alias: Telegram moje kategorie
    trigger:
      - platform: event
        event_type: telegram_callback
        event_data:
          command: /callback_moje
    action:
      - service: telegram_bot.send_message
        data:
          target: "{{ trigger.event.data.chat_id }}"
          parse_mode: html
          message: |
            <b>🎯 Moje kategorie</b>
            
            Zde můj vlastní obsah...
          inline_keyboard:
            - "🔄 Refresh:/callback_moje, 🏠 Menu:/callback_menu"
```

Pak přidej tlačítko do hlavního menu:

```yaml
inline_keyboard:
  - "🎯 Moje:/callback_moje, ..."
```

### Úprava vzhledu zpráv

Používá se HTML formatting:
- `<b>Tučně</b>` 
- `<i>Kurzíva</i>`
- `<code>Kód</code>`
- `&lt;` pro `<` a `&gt;` pro `>`

### Filtrování entit

Příklad - zobrazit jen světla z ložnice:

```yaml
{% set lights = states.light 
   | selectattr('entity_id', 'search', 'bedroom') 
   | list %}
```

## 🐛 Troubleshooting

### Menu nefunguje

1. **Zkontroluj Telegram bot konfiguraci:**
```yaml
# configuration.yaml
telegram_bot:
  - platform: polling
    api_key: YOUR_API_KEY
    allowed_chat_ids:
      - YOUR_CHAT_ID
```

2. **Ověř že packages jsou povolené:**
```yaml
homeassistant:
  packages: !include_dir_named packages
```

3. **Zkontroluj logy:**
```
Nastavení → Systém → Logy
```

### Tlačítko "Menu" nefunguje

Ujisti se, že máš automatizaci `Telegram: Menu callback` v souboru.

### Některé sekce jsou prázdné

To je normální - pokud nemáš dané entity (např. vysavače, kalendář), sekce bude prázdná nebo zobrazí "nenalezeno".

### Chybové hlášky v logu

```
Template variable error: 'list object' has no attribute 'attributes'
```

➜ Některá entita není dostupná. Kód je navržen tak, aby tyto chyby ignoroval.

### Zprávy jsou příliš dlouhé

Telegram má limit 4096 znaků. Pokud máš hodně entit, uprav template pro zkrácení výstupu:

```yaml
{% if sensors | count > 10 %}
({{ sensors|count }} sensorů)
{% else %}
# zobraz seznam
{% endif %}
```

## 📝 Tipy a triky

### Rychlé otevření menu

Můžeš si v Telegramu přidat tlačítka:
1. Napiš botovi `/setcommands`
2. Pošli:
```
menu - Hlavní menu
status - Rychlý přehled
thp - Teplota/vlhkost/tlak
air - Kvalita vzduchu
```

### Notifikace při problémech

Přidej automatizaci která pošle zprávu při problému:

```yaml
automation:
  - alias: Notify low battery
    trigger:
      - platform: numeric_state
        entity_id: sensor.smoke_detector_battery
        below: 20
    action:
      - service: telegram_bot.send_message
        data:
          message: "⚠️ Nízká baterie: {{ trigger.to_state.name }}"
```

### Pravidelný report

Denní souhrn v 8:00:

```yaml
automation:
  - alias: Morning report
    trigger:
      - platform: time
        at: "08:00:00"
    action:
      - service: telegram_bot.send_message
        data:
          message: |
            🌅 Dobré ráno!
            
            Teplota venku: {{ states('sensor.outdoor_temp') }}°C
            Spotřeba včera: {{ states('sensor.energy_yesterday') }} kWh
            
            /menu pro více info
```

## 🤝 Přispění

Máš nápad na vylepšení? 
- Otevři issue
- Pošli pull request
- Sdílej vlastní úpravy

## 📄 Licence

MIT License - volně použitelné a upravitelné

## 🔗 Užitečné odkazy

- [Home Assistant Telegram Bot](https://www.home-assistant.io/integrations/telegram_bot/)
- [Telegram Bot API](https://core.telegram.org/bots/api)
- [HA Templates](https://www.home-assistant.io/docs/configuration/templating/)
- [HA Packages](https://www.home-assistant.io/docs/configuration/packages/)

---

**Verze:** 1.0  
**Autor:** Komunita Home Assistant  
**Datum:** 2025
