# MEXESS Tracker — Meta Ads Goal (€30 000/месец)

Репо-източник на истината за целта, разходите и прогреса. Поддържа се автоматично от два Claude Code Routine-а.

## Структура

```
mexess-tracker/
├── costs.json              # Икономика: цели, euShipments тарифи, COGS, тегла (редактираш ръчно при промяна)
├── data.json               # Дневни записи — пише го Routine 1 (не пипай ръчно)
├── dashboard.html          # Дашбордът — отваря се през GitHub Pages
├── reports/                # Markdown отчети от Routine 2 (пон + чет)
├── routine-1-daily.md      # Промпт за Routine 1
└── routine-2-optimization.md # Промпт за Routine 2
```

## Настройка (еднократно, ~10 мин)

1. **Създай private GitHub репо** `mexess-tracker` и качи всички файлове от този пакет
   (папката `reports/` може да е празна — добави `.gitkeep`).

2. **GitHub Pages** (за дашборда): Settings → Pages → Deploy from branch → `main` / root.
   Дашбордът ще е на `https://<user>.github.io/mexess-tracker/dashboard.html`.
   Забележка: при private репо Pages изисква платен GitHub план — алтернативно направи репото public
   (данните са само агрегати без лични данни) или отваряй dashboard.html локално.

3. **Създай Routine 1** на claude.ai/code/routines (или /schedule в CLI):
   - Промпт: съдържанието на `routine-1-daily.md`
   - График: всеки ден 08:00 Europe/Sofia
   - Репо: `mexess-tracker` · Конектори: Meta Ads + Shopify

4. **Създай Routine 2**:
   - Промпт: съдържанието на `routine-2-optimization.md`
   - График: понеделник и четвъртък 08:30 Europe/Sofia
   - Репо + конектори: същите

5. **Провери след първия run**: има ли нов entry в `data.json`, зарежда ли дашбордът,
   и че routine-ът НЕ е правил промени по рекламния акаунт.

## Целите (от costs.json)

| Показател | Цел |
|---|---|
| Оборот | €30 000/месец |
| MER | ≥ 3.0 (stretch 3.5) |
| CPP | €12–14.5 |
| Рекламен бюджет | €8 500–10 000 |
| Печалба | €7 000–10 000 |

При промяна на цени, тарифи или цели — редактирай само `costs.json`; двата routine-а го четат при всеки run.
