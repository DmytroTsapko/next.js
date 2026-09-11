# SOURCE.md — единый источник истины
# Проект: Deriv Bots / Strategies / Logging
# Владелец: Дмитро
# Лицензия: личное использование, без коммерции

## МЕТА
version: 1.0
created: 2026-09-11
updated: 2026-09-11
scope: Deriv API, торговые боты, стратегии, логирование, RAG
language: ru
owner_token_alias: "my-demo-token"  # никогда не вставлять сам токен

---

## ПРАВИЛА ДЛЯ AI

Эти правила обязательны для любого ассистента, читающего этот файл.

1. **CONFIRMED** — использовать как истину без оговорок.
2. **CLAIMED** — помечать как «непроверено», не использовать в генерации кода без предупреждения.
3. **REFERENCE** — только для трассировки, не как источник фактов.
4. **Имя «AI», «Agent», «Model» в названии продукта ≠ наличие ИИ.** Требуется артефакт (модель, веса, API к LLM).
5. **Не выдумывать.** Если данных нет — сказать прямо: «нет в SOURCE.md».
6. **При генерации кода** опираться только на CONFIRMED. Если нужно CLAIMED — явно предупредить.
7. **Все новые факты** сначала попадают в CLAIMED. После проверки на демо → CONFIRMED.

---

## CONFIRMED

Проверенные факты. Источник: официальная документация, тесты на демо, наблюдения.

### Deriv API — подключение
```yaml
- id: deriv-ws-url
  claim: "WebSocket endpoint: wss://ws.derivws.com/websockets/v3?app_id={app_id}"
  source: "https://api.deriv.com/docs"
- id: deriv-auth
  claim: "Авторизация через токен, созданный в Settings → API Token"
  source: "личный кабинет Deriv"
- id: deriv-demo
  claim: "Демо-счёт переключается в интерфейсе, токен работает и для demo, и для real"
  source: "тест"
```

### Deriv API — методы
```yaml
- id: deriv-method-ticks
  claim: "ticks — подписка на котировки"
- id: deriv-method-candles
  claim: "candles — исторические свечи (granularity в секундах)"
- id: deriv-method-proposal
  claim: "proposal — получить цену контракта до покупки"
- id: deriv-method-buy
  claim: "buy — купить контракт, принимает price и parameters"
- id: deriv-method-balance
  claim: "balance — текущий баланс"
- id: deriv-method-poc
  claim: "proposal_open_contract — результат сделки"
```

### Стратегии — базовые фильтры
```yaml
- id: strat-sma20
  claim: "SMA(20) на минутных свечах — фильтр направления тренда"
  rule: "close > SMA → только CALL; close < SMA → только PUT"
- id: strat-body-range
  claim: "body/range ≥ 0.75 — подтверждение сильной свечи"
  rule: "тело свечи / полный диапазон ≥ 0.75"
- id: strat-body-avg
  claim: "тело последней свечи > среднего тела 5 предыдущих"
- id: strat-stake-fixed
  claim: "фиксированная ставка 2–3% от депозита, без мартингейла"
- id: strat-stop-loss
  claim: "стоп-лосс -10% от начального депозита за сессию"
- id: strat-demo-first
  claim: "любая новая стратегия сначала тестируется на демо-счёте"
```

### Логирование
```yaml
- id: log-format
  claim: "формат log.jsonl — одна строка = одно событие"
- id: log-fields
  claim: "поля: time, bot, signal, reason, stake, result, market_state"
```

### Tuplemint — подтверждено из открытых источников
```yaml
- id: tuplemint-platform
  claim: "AI-конструктор ботов для Deriv, промпт на английском → готовый бот"
  source: "https://github.com/safebinarybot/tuplemint"
- id: tuplemint-prompts
  claim: "Примеры промптов: martingale, RSI, digit patterns"
  source: "README tuplemint"
- id: tuplemint-risk
  claim: "Заявлено: риск ≤2% на сделку, дневной лимит убытка, адаптивный стейкинг"
  source: "README tuplemint"
```

---

## CLAIMED

Заявления без независимой проверки. Использовать с осторожностью.

### Винрейты стратегий (Tuplemint)
```yaml
- id: tuplemint-double-zero
  claim: "Double Zero Difference — 93% винрейт"
  status: CLAIMED
  note: "не проверено на демо"
- id: tuplemint-even-digit
  claim: "Even Digit Dominance — 80%"
  status: CLAIMED
- id: tuplemint-martingale
  claim: "Martingale Master — 75%"
  status: CLAIMED
- id: tuplemint-rsi
  claim: "RSI Reversal — 68%"
  status: CLAIMED
- id: tuplemint-ma-cross
  claim: "Moving Average Crossover — 65%"
  status: CLAIMED
```

### NextTrader
```yaml
- id: nextrader-bot-url
  claim: "bot.nextrader.live — веб-приложение для торговли на Deriv"
  status: CLAIMED
- id: nextrader-logic
  claim: "использует SMA(20), body/range ≥ 0.75, сравнение с avg body 5"
  status: CLAIMED
  note: "описано в открытом чате, требует проверки"
```

### Обещания приложений
```yaml
- id: promise-24-7
  claim: "торговля 24/7 без ручного вмешательства"
  status: CLAIMED
- id: promise-demo
  claim: "тестирование на демо перед реальной торговлей"
  status: CLAIMED
```

---

## REFERENCE

Ссылки для трассировки. Не источники фактов.

```yaml
- id: ref-deriv-docs
  url: "https://api.deriv.com/docs"
- id: ref-tuplemint
  url: "https://github.com/safebinarybot/tuplemint"
- id: ref-nextrader
  url: "https://bot.nextrader.live/#free_bots"
- id: ref-chatgpt-share-1
  url: "https://chatgpt.com/share/6aa0d3f0-a454-83eb-9516-6e2c3f678a2b"
- id: ref-chatgpt-share-2
  url: "https://chatgpt.com/share/6aa0d363-658c-83eb-bed2-1764ef827591"
```

---

## АРХИТЕКТУРА ИЗВЛЕЧЕНИЯ ДОКАЗАТЕЛЬСТВ

Правила, по которым факт попадает в CONFIRMED.

```yaml
rule-1:
  name: "Только артефакт считается доказательством"
  description: "Название AI/agent/model ≠ наличие ИИ. Нужен артефакт: веса, API к LLM, код модели."
rule-2:
  name: "Двойная проверка"
  description: "Факт переходит из CLAIMED в CONFIRMED только после проверки на демо или подтверждения в официальной документации."
rule-3:
  name: "Трассировка"
  description: "Каждый CONFIRMED имеет source — ссылку или запись теста."
rule-4:
  name: "Устаревание"
  description: "CONFIRMED пересматривается при изменении API или поведения рынка."
```

---

## ЛОГИ (пример формата)

Файл log.jsonl. Одна строка = одно событие.

```jsonl
{"time":"2026-09-11T10:00:00Z","bot":"custom-sma","signal":"CALL","reason":"close>SMA(20), body/range=0.82","stake":2.00,"result":"win","market_state":"trending_up"}
{"time":"2026-09-11T10:01:00Z","bot":"custom-sma","signal":"skip","reason":"body/range=0.40","stake":0,"result":"none","market_state":"flat"}
{"time":"2026-09-11T10:02:00Z","bot":"custom-sma","signal":"PUT","reason":"close<SMA(20), body/range=0.91","stake":2.00,"result":"loss","market_state":"trending_down"}
```

Поля обязательные:

- time — ISO 8601
- bot — имя бота
- signal — CALL / PUT / skip
- reason — текстовая причина (какой фильтр сработал)
- stake — ставка
- result — win / loss / none
- market_state — trending_up / trending_down / flat / volatile

---

## ЦИКЛ САМОСОВЕРШЕНСТВОВАНИЯ

```text
1. CODEX пишет/правит скрипт
        ↓
2. Скрипт работает на демо, пишет log.jsonl
        ↓
3. Логи загружаются в ChatGPT Project (вместе с SOURCE.md)
        ↓
4. Промпт: "Найди закономерности в log.jsonl. Где бот ошибается? Какие фильтры добавить?"
        ↓
5. Новые выводы → в CLAIMED
        ↓
6. Проверка на новой выборке демо → CONFIRMED
        ↓
7. CODEX правит скрипт по CONFIRMED
        ↓
   Повтор
```

---

## ПРОМПТЫ ДЛЯ AI (готовые)

### Для CODEX — добавление логирования

«Добавь в скрипт запись каждого решения в log.jsonl. Одна строка = одно событие. Поля: time, bot, signal, reason, stake, result, market_state. Если файла нет — создай. Формат — JSON Lines.»

### Для ChatGPT Project — анализ логов

«Прочитай SOURCE.md и log.jsonl. Используй только CONFIRMED. Найди закономерности: при каких market_state бот ошибается чаще? Какие фильтры добавить? Ответ оформи как новые записи для раздела CLAIMED.»

### Для генерации нового бота

«Опираясь только на CONFIRMED из SOURCE.md, напиши Python-скрипт: подключение к Deriv API через WebSocket, SMA(20) фильтр, body/range ≥ 0.75, фиксированная ставка 2%, стоп-лосс -10%. Логирование в log.jsonl. Если нужно CLAIMED — предупреди.»

### Для проверки факта

«Проверь утверждение: [текст]. Если оно есть в CONFIRMED — подтверди. Если в CLAIMED — пометь как непроверенное. Если нет — скажи "нет в SOURCE.md".»

---

## ЖУРНАЛ ИЗМЕНЕНИЙ

```yaml
- date: 2026-09-11
  change: "Создан SOURCE.md v1.0. Добавлены CONFIRMED, CLAIMED, REFERENCE, правила, промпты, цикл."
- date: [дата]
  change: "[что добавили]"
```

---

## ЗАПРЕТЫ

```yaml
- "Не вставлять реальные API-токены в этот файл. Только alias."
- "Не публиковать SOURCE.md с реальными логинами/паролями."
- "Не использовать чужие токены из декомпилированных APK."
- "Не распространять модифицированные APK."
- "Не считать CLAIMED доказанным без проверки на демо."
```

---

## КОНТАКТ / ВЛАДЕЛЕЦ

owner: Дмитро
repo: https://github.com/DmytroTsapko/next.js
purpose: "личное использование, обучение, не коммерция"
