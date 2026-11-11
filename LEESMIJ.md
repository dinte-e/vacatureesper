# Vacature-alert (Esper)

Elke ochtend een mail met nieuwe vacatures als producer: brand & campaign production, events en brand activations, brand partnerships, content-/e-commerceproductie en digital asset management. Elke vacature wordt maar één keer gemeld.

## Bestanden

| Bestand | Wat |
| --- | --- |
| `vacature_alert.py` | Het script. Hetzelfde als in Dinte's repo, alleen het mailonderwerp zegt "je zoektocht". |
| `config.json` | Zoektermen, uitsluitingen en alle feeds. De Google Alert-links komen hier. |
| `google_alerts.txt` | Optioneel: links mogen ook hier, zonder aanhalingstekens. |
| `.github/workflows/vacature-alert.yml` | Draait het script elke dag om 06:00 UTC. |
| `gezien.json` | Maakt het script zelf aan bij de eerste run. |

## Instellen

1. **Secrets:** *Settings → Secrets and variables → Actions*. Maak `SMTP_USER`, `SMTP_PASSWORD` en `MAIL_TO` aan (Espers adres), plus `SMTP_HOST`/`SMTP_PORT` of de Telegram-secrets als je die bij Dinte ook gebruikt.
2. **Google Alert-links:** Esper maakt de 12 alerts aan en stuurt de RSS-links. Vervang in `config.json` elke `PLAK_HIER_DE_RSS_LINK` door een link en laat de aanhalingstekens en komma's staan.
3. **Testen:** *Actions → Vacature-alert → Run workflow*. Kies `test-melding` om de mail te testen, `test-feeds` om te zien welke feeds werken, en daarna `normaal`.

Tot de links zijn ingevuld draait alleen de feed van Culturele vacatures.

## Aanpassen

- `zoektermen`: een titel moet minstens één van deze termen bevatten. Een `*` aan het eind betekent "begint met", aan het begin "eindigt met".
- `uitsluiten_als_in_titel`: stages, junior, assistant, fabriekswerk, winkelfuncties. Senior, lead en head of blijven bewust staan. Let op: `*stage` filtert ook *Stage Manager*.
- `voorkeursplaatsen`: deze plaatsen worden in de mail gemarkeerd.
