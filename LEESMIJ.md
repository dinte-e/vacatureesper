# Vacature-alert (Esper)

Elke ochtend een mail met nieuwe vacatures als producer: brand & campaign production, events en brand activations, brand partnerships, content-/e-commerceproductie en digital asset management. Elke vacature wordt maar één keer gemeld.

## Bestanden

| Bestand | Wat |
| --- | --- |
| `vacature_alert.py` | Het script. Hetzelfde als in Dinte's repo, alleen het mailonderwerp zegt "je zoektocht". |
| `config.json` | Zoektermen, uitsluitingen en alle feeds, inclusief Espers 15 Google Alerts. |
| `google_alerts.txt` | Optioneel: links mogen ook hier, zonder aanhalingstekens. |
| `.github/workflows/vacature-alert.yml` | Draait het script elke dag om 06:00 UTC. |
| `gezien.json` | Maakt het script zelf aan bij de eerste run. |

## Instellen

1. **Secrets:** *Settings → Secrets and variables → Actions*. Maak `SMTP_USER`, `SMTP_PASSWORD` en `MAIL_TO` aan (Espers adres), plus `SMTP_HOST`/`SMTP_PORT` of de Telegram-secrets als je die bij Dinte ook gebruikt.
2. **Testen:** *Actions → Vacature-alert → Run workflow*. Kies eerst `test-feeds` om te zien of alle 16 feeds werken, dan `test-melding` om de mail te testen.
3. **Eerste echte run:** `normaal` stuurt alles wat er nu in de feeds staat. Wil je met een lege lei beginnen, draai dan eerst `stil`: dat markeert alles als gezien zonder mail.

Een nieuwe Google Alert toevoegen: kopieer in `config.json` een blok onder `feeds` en vervang naam, zoekopdracht en url. Of plak alleen de link in `google_alerts.txt`.

## Aanpassen

- `zoektermen`: een titel moet minstens één van deze termen bevatten. Een `*` aan het eind betekent "begint met", aan het begin "eindigt met".
- `uitsluiten_als_in_titel`: stages, junior, assistant, fabriekswerk, winkelfuncties. Senior, lead en head of blijven bewust staan. Let op: `*stage` filtert ook *Stage Manager*.
- `voorkeursplaatsen`: deze plaatsen worden in de mail gemarkeerd.
- Vier alerts staan in Google op *alle regio's* (fashion- & sportmerken 1 en 2, Fashion / PR agencies, beauty brands). Komen er te veel buitenlandse vacatures binnen, zet die alerts dan in Google op *Nederland*; de link blijft hetzelfde.
