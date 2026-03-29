# Българска Фондация за Киберсигурност — csf.bg

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Static Site](https://img.shields.io/badge/Type-Static%20HTML-beige)](https://csf.bg)
[![Language: BG](https://img.shields.io/badge/Language-Bulgarian-green)](https://csf.bg)

Официалният уебсайт на **Българска Фондация за Киберсигурност** —
водещата общностна организация за киберсигурност в България.

> Образование · Кариерно развитие · Актуални заплахи · Общност от специалисти

---

## За проекта

Сайтът е **изцяло статичен** — нито build инструменти, нито npm, нито frameworks.
Всяка страница е самостоятелен `.html` файл, зареждащ само два Google Fonts.
Всичко останало е чист CSS custom properties + vanilla JS.

### Цел

| Аудитория | Какво намира |
|---|---|
| Начинаещи | Кариерни пътеки, безплатни ресурси, ментор |
| Специалисти | Заплати, компании, сертификации, събития |
| Работодатели | Директория, партньорство, обяви |
| Граждани | Актуални заплахи, awareness материали |

---

## Структура

```
csf-bg/
├── index.html              ← Начална страница (пълна)
├── README.md               ← Този файл
├── SKILL.md                ← Design system + component guide за AI/разработчици
│
├── resursi/
│   ├── organizacii.html    ← Директория организации
│   ├── forumi.html         ← Форуми и общности
│   ├── zaplahi.html        ← Заплахи и инциденти
│   ├── instrumenti.html    ← Инструменти
│   ├── ctf.html            ← CTF ресурси и платформи
│   ├── knigi.html          ← Препоръчани книги
│   └── video.html          ← Видео ресурси и канали
│
├── obuchenie/
│   ├── universiteti.html   ← Университетски програми в БГ
│   ├── onlain-kursove.html ← Онлайн курсове и платформи
│   ├── sertifikacii.html   ← Ръководство по сертификации
│   └── platformi.html      ← Практически платформи (HTB, THM…)
│
├── kariera/
│   ├── mentorstvo.html     ← Менторска програма
│   ├── kompanii.html       ← Директория компании (55+)
│   ├── profesii.html       ← 6 кариерни пътеки
│   └── zaplati.html        ← Заплати в сектора
│
├── sabitia.html            ← Календар на събития
└── vklyuchi-se.html        ← Членство и включване
```

---

## Дизайн система

Пълната дизайн система, компонентна библиотека и правила за разработка са документирани в **[SKILL.md](SKILL.md)**.

### Бързо резюме

**Цветова палитра:**
- Основен фон: `#FAF8F3` (cream) и `#F4EFE4` (beige)
- Навигация / Hero: `#0D1F3C` (navy)
- Акценти: `#2B5BB5` (blue)
- Текст: `#1C120A` (espresso) → `#4A3020` (brown) → `#7A5C3C` (bark)

**Шрифтове:**
- Заглавия: [Cormorant Garamond](https://fonts.google.com/specimen/Cormorant+Garamond)
- UI: [DM Sans](https://fonts.google.com/specimen/DM+Sans)

---

## Навигация

```
За нас
Ресурси ▾   Организации · Форуми · Заплахи · Инструменти · CTF · Книги · Видео ресурси
Обучение ▾  Университетски програми · Онлайн курсове · Сертификации · Платформи
Кариера ▾   Менторство · Компании · Професионални пътеки · Заплати
Събития
Включи се
```

---

## Как да добавиш нова страница

1. Копирай `index.html` → нов файл в съответната папка
2. Запази `<head>` с Google Fonts непроменен
3. Запази целия `<nav>` и `#mobile-menu` непроменени
4. Запази `<footer>` непроменен
5. Добави `class="active"` на съответния nav линк
6. Замени само съдържанието между `.mission-strip` и `.partners-section`

---

## Съдържателни правила

- **Заплатите се посочват само в EUR** — никога в BGN
- **Основен език: Български** — английски само за технически термини и имена
- **Статистиките трябва да са реални** — от CERT.BG, cybercrime.bg, ENISA, или проучването на пазара на труда
- **Кариерни пътеки:** 6 пътеки — Имплементиране, Опериране, Риск, Тестване, Анализ, Лидерство
- **Директория:** 55+ компании (български + международни с офис в България)

---

## Ключови данни за съдържание

| Показател | Стойност | Източник |
|---|---|---|
| Специалисти в сектора | ~3,500+ | Оценка пазар на труда |
| Активни обяви | 60–92 | DEV.BG, Jobs.bg, LinkedIn |
| Компании в директория | 55+ | Ръчна верификация |
| Университетски програми | 10+ | Официални сайтове |
| Месечни срещи CSTB | 45+ | cybersecuritytalks.bg |
| BEC загуби България 2024 | €12M | Cybercrime.bg / GDBOP |
| Засегнати от ransomware 2025 | 20+ компании | CERT.BG |

### Диапазони на заплати (EUR нето/месец)

| Ниво | Диапазон |
|---|---|
| Junior (0–2г) | €1,000–1,800 |
| Mid (2–5г) | €1,800–2,800 |
| Senior (5–10г) | €2,500–4,100 |
| Expert/Lead (10г+) | €3,600–6,100 |
| CISO / Director | €5,100–11,200+ |

---

## Партньори

| Организация | URL | Тип |
|---|---|---|
| XaKeP.bg | https://xakep.bg | Общност |
| Cyber Security Talks Bulgaria | https://cybersecuritytalks.bg | Месечни срещи |
| Cybercrime.bg | https://cybercrime.bg | ГДБОП · МВР |
| BSides Sofia | https://securitybsides.bg | Конференция |
| ISSA Bulgaria | https://issa-bulgaria.eu | Асоциация |
| ISACA Sofia Chapter | https://isaca-sofia.org | Сертификации |

---

## Свързани ресурси

- [Проучване на пазара на труда (gist)](https://gist.github.com/miglen/f302d1230921c0156abab2c2bd53e402) — заплати и обяви
- [cybercrime.bg](https://cybercrime.bg) — официална платформа за киберпрестъпност (ГДБОП)
- [Comprehensive Research Report](docs/research-report.md) — пълен анализ на екосистемата (100+ организации, университети, сертификации)
- [ENISA Threat Landscape](https://enisa.europa.eu/topics/cyber-threats/etl) — EU заплахи
- [CERT.BG](https://govcert.bg) — национален CSIRT

---

## Разработка

```bash
# Клонирай репото
git clone https://github.com/csf-bg/csf-bg.git
cd csf-bg

# Стартирай локален сървър (Python)
python3 -m http.server 8000

# Или с Node
npx serve .

# Отвори в браузъра
open http://localhost:8000
```

Няма нужда от build стъпка. Редактирай HTML директно и опресни браузъра.

---

## Лиценз

MIT © 2024 Българска Фондация за Киберсигурност — ЕИК 206640938

---

*Изграждаме по-сигурно дигитално бъдеще за България.*
