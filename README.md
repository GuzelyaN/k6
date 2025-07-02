# k6
---
## Preconditions

1. Зайди на официальный сайт https://k6.io/docs/getting-started/installation/#windows
2. Скачай последний .zip с https://github.com/grafana/k6/releases
3. Распакуй архив, например в C:\k6
4. Добавь путь к папке с k6.exe в системную переменную окружения PATH


## ✅ Шаг 1. Установи `postman-to-k6`

Это инструмент, который конвертирует Postman коллекции в формат, понятный k6.

```bash
npm install -g postman-to-k6
```

---

## ✅ Шаг 2. Экспортируй коллекцию и окружение из Postman

1. Зайди в Postman → нужная коллекция → кликни `...` → `Export`.

   * Выбери **v2.1 (Collection format)**.
2. То же самое сделай с **Environment** → экспорт `.json`.

---

## ✅ Шаг 3. Конвертируй Postman → k6

```bash
postman-to-k6 your_collection.json -e your_environment.json -o script.js
```

* `your_collection.json` — экспортированная коллекция.
* `your_environment.json` — экспорт окружения (опционально).
* `script.js` — выходной файл, пригодный для запуска в k6.
// коряво конвертирует
---

## ✅ Шаг 4. Запусти сконвертированный скрипт в k6

```bash
k6 run script.js
```

Можно сразу задать количество виртуальных пользователей и длительность теста:

```bash
k6 run --vus 50 --duration 1m script.js
```

Можно записать результаты в файл

```bash
k6 run script.js > output.txt  
```
Указать baseURL
```bash
k6 run --vus 50 --duration 1m -e baseUrl=https://***-backend-prod.fly.dev script.js
```
