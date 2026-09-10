---
name: maysoulme-presentation
description: Создаёт HTML-презентацию для видеоуроков в фирменном стиле maysoulme (60/40 split, схемки-вариации)
---

# Скилл: Оформление презентации для видеоуроков maysoulme

Когда пользователь просит создать презентацию, слайды или материал для видеоурока — создай HTML-страницу со слайдами в фирменном стиле maysoulme.

## Формат

Это **презентация для видеоуроков**. Каждый слайд — отдельный экран 100vh. Макет разделён вертикально:
- **Левые 60%** — зона контента (текст, списки, карточки)
- **Правые 40%** — пустая зона под видео (туда в монтаже вставляется видео автора)
- Между ними — тонкая вертикальная линия-разделитель `#e5dccf`

Правая часть ВСЕГДА пустая. Никогда не размещай туда контент.

## Бренд-стиль

### Цвета
- Фон: `#ffffff`
- Текст: `#1a1a1a`
- Текст второстепенный: `#4a4238`, `#6b6157`
- Акцент (коричневый): `#6b4f35` — для курсивных выделений в заголовках, точек в списках, бейджей
- �бежевые блоки: `#f5f0e8` — без закруглений, без цветных линий
- Карточки: `#faf6f0` с рамкой `#e5dccf` — квадратные углы
- На тёмном фоне НИКОГДА не использовать коричневый — заменять на `#c9a07a`

### Шрифты (Google Fonts)
```html
<link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Inter:wght@400;500;600;700;800&family=DM+Sans:ital@1&display=swap" rel="stylesheet">
```
- **Заголовки**: `Libre Baskerville`, Georgia, serif — жирный, с курсивными акцентами коричневым
- **Основной текст**: `Inter`, sans-serif — 16px, line-height 1.75
- **Подзаголовки**: `Libre Baskerville` — 20px, жирный
- **Декоративные цифры**: `Libre Baskerville`, italic, opacity 0.25, цвет `#6b4f35` — для нумерованных списков и метрик
- **Ник maysoulme**: `DM Sans`, italic, `#948a7c`

### Навбар (на каждом слайде)
- Ширина = 60% (только зона контента)
- Логотип MS слева, текст *maysoulme* справа
- Логотип: `<img src="https://maiyamaiya19999-bit.github.io/maysoulme-assets/logo-ms.png" alt="MS">` высота 30px
- Текст maysoulme: DM Sans italic, 14px, цвет `#948a7c`, с `margin-right: 8px`
- Тонкая линия снизу `#f0e9df`

### Бейдж (на титульном слайде)
- Тонкая рамка 1px коричневая, текст капсом, разрядка 2px, размер 11px
- Текст: «УРОК», «ГАЙД», «КУРС» и т.п.

## Структура слайдов

### Слайд 1 — Титульный
```
Навбар
Бейдж «УРОК»
Заголовок h1 (Libre Baskerville, 36px, с курсивным акцентом коричневым)
Описание (Inter, 17px, #6b6157)
Мета-инфо (13px, #a39889, с разрядкой)
```

### Слайды 2+ — Контентные
```
Навбар
Заголовок h2 (Libre Baskerville, 28px) — БЕЗ нумерации
Контент: текст, списки, блоки, карточки, схемки
```

## Важные правила

1. **БЕЗ нумерации** — никаких 01., 02., 03. в заголовках слайдов
2. **БЕЗ номеров страниц** — никаких «1 / 21» внизу
3. **Контент только в левых 60%** — правая часть всегда пустая
4. **Каждый слайд = 100vh** — один экран
5. **Навбар на каждом слайде** — не sticky, просто повторяется
6. **Квадратные углы везде** — никаких border-radius
7. **max-width: 580px** для внутреннего контента слайда
8. **Контент вертикально по центру** слайда (flexbox align-items: center)
9. **Чередуй типы слайдов** — не делай 5 одинаковых слайдов подряд. Разбавляй базовые слайды (текст, списки) схемками (цитаты, метрики, чек-листы, формулы и т.д.). Каждый 2–3-й слайд должен быть схемкой, чтобы презентация была визуально разнообразной и интересной.
10. **Claude и Reels** — слова «клод» и «рилс» ВСЕГДА пишутся на английском: **Claude** и **Reels**. Никогда не писать кириллицей.

---

## Базовые элементы контента

### Заголовок секции
```html
<h2 class="section-heading">Текст заголовка <em>акцентная часть</em></h2>
```
Слово или фраза в `<em>` выделяется курсивом и коричневым цветом.

### Серый блок .highlight
Для ключевых мыслей, выводов, важных замечаний.
```html
<div class="highlight"><strong>Важно:</strong> текст блока</div>
```

### Список .guide-list
С коричневыми точками, разделителями между пунктами.
```html
<ul class="guide-list">
  <li><strong>Жирный пункт.</strong> Пояснение к пункту.</li>
</ul>
```

### Подзаголовок .sub-heading
```html
<h3 class="sub-heading">Подзаголовок</h3>
```

### Карточка .scenario-card
Для сценариев, кейсов, примеров.
```html
<div class="scenario-card">
  <div class="scenario-card__num">ЗАГОЛОВОК КАРТОЧКИ</div>
  <div class="scenario-card__title">Название</div>
  <div class="scenario-card__point">
    <span class="scenario-card__point-label">Метка.</span>
    <span class="scenario-card__point-text">Текст пункта.</span>
  </div>
  <div class="scenario-card__tip"><strong>Совет:</strong> текст совета</div>
</div>
```

### Завершающая фраза .footer-note
Курсивная фраза Libre Baskerville для финального слайда.
```html
<p class="footer-note">Текст <em>акцент</em></p>
```

---

## Схемки-вариации (8 типов)

Используй эти схемки для разнообразия. Чередуй их с базовыми слайдами — каждый 2–3-й слайд должен быть одной из этих схемок. Выбирай тип по смыслу контента.

### Схемка 1: Цитата-акцент
Для ключевых мыслей, ярких высказываний, выводов.
```html
<div class="slide__inner">
  <div class="quote-slide__label">КЛЮЧЕВАЯ МЫСЛЬ</div>
  <div class="quote-slide__mark">&ldquo;</div>
  <div class="quote-slide__text">Текст цитаты с <em>акцентом</em></div>
  <div class="quote-slide__divider"></div>
  <p class="quote-slide__source">Пояснение или контекст цитаты.</p>
</div>
```

### Схемка 2: Шаги с вертикальной линией
Для пошаговых процессов, путей, последовательностей. Точки: заполненные = пройденные (`steps__item--active`), пустые = предстоящие.
```html
<div class="slide__inner">
  <div class="steps__heading">Заголовок <em>акцент</em></div>
  <div class="steps__list">
    <div class="steps__item steps__item--active">
      <div class="steps__dot"></div>
      <div class="steps__item-title">Шаг 1</div>
      <div class="steps__item-text">Описание шага.</div>
    </div>
    <div class="steps__item">
      <div class="steps__dot"></div>
      <div class="steps__item-title">Шаг 2</div>
      <div class="steps__item-text">Описание шага.</div>
    </div>
  </div>
</div>
```

### Схемка 3: Нумерованный список
Для пронумерованных пунктов, анатомий, структур. Цифры — крупные, Libre Baskerville italic, полупрозрачные.
```html
<div class="slide__inner">
  <div class="numlist__heading">Заголовок <em>акцент</em></div>
  <div class="numlist__item">
    <div class="numlist__num">1</div>
    <div class="numlist__text"><strong>Название</strong> <span>— описание пункта.</span></div>
  </div>
  <div class="numlist__item">
    <div class="numlist__num">2</div>
    <div class="numlist__text"><strong>Название</strong> <span>— описание пункта.</span></div>
  </div>
</div>
```

### Схемка 4: Акцентная полоса слева
Для главных правил, ключевых принципов, важных мыслей с пояснением.
```html
<div class="slide__inner">
  <div class="accent-bar__label">ЛЕЙБЛ СВЕРХУ</div>
  <div class="accent-bar__block">
    <div class="accent-bar__title">Заголовок <em>акцент</em></div>
    <p class="accent-bar__text">Основной текст с пояснением.</p>
    <div class="accent-bar__footer">Курсивная подпись внизу</div>
  </div>
</div>
```

### Схемка 5: Чек-лист (Делай / Не делай)
Для сравнений, правильного и неправильного подхода, do/don't.
```html
<div class="slide__inner">
  <div class="checklist__heading">Заголовок — <em>акцент</em></div>
  <div class="checklist__grid">
    <div class="checklist__col">
      <div class="checklist__col-label checklist__col-label--do">Делай</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--do">&#x2713;</span>Пункт</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--do">&#x2713;</span>Пункт</div>
    </div>
    <div class="checklist__col">
      <div class="checklist__col-label checklist__col-label--dont">Не делай</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--dont">&#x2717;</span>Пункт</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--dont">&#x2717;</span>Пункт</div>
    </div>
  </div>
</div>
```

### Схемка 6: Три метрики
Для цифр, статистики, ключевых показателей. Цифры — Libre Baskerville italic, полупрозрачные.
```html
<div class="slide__inner">
  <div class="metrics__heading">Заголовок <em>акцент</em></div>
  <div class="metrics__row">
    <div class="metrics__item">
      <div class="metrics__number">3</div>
      <div class="metrics__label">секунды</div>
      <div class="metrics__desc">Пояснение к цифре.</div>
    </div>
    <div class="metrics__item">
      <div class="metrics__number">80%</div>
      <div class="metrics__label">успеха</div>
      <div class="metrics__desc">Пояснение к цифре.</div>
    </div>
    <div class="metrics__item">
      <div class="metrics__number">2+</div>
      <div class="metrics__label">триггера</div>
      <div class="metrics__desc">Пояснение к цифре.</div>
    </div>
  </div>
</div>
```

### Схемка 7: Вопрос-ответ
Для FAQ, частых вопросов, разбора сомнений. Знаки `?` — Libre Baskerville 28px italic.
```html
<div class="slide__inner">
  <div class="qa__heading">Заголовок <em>акцент</em></div>
  <div class="qa__item">
    <div class="qa__question">Текст вопроса?</div>
    <div class="qa__answer">Текст ответа.</div>
  </div>
  <div class="qa__item">
    <div class="qa__question">Текст вопроса?</div>
    <div class="qa__answer">Текст ответа.</div>
  </div>
</div>
```

### Схемка 8: Формула
Для визуальных формул, уравнений (A + B = C). Серые блоки для компонентов, коричневая рамка для результата.
```html
<div class="slide__inner">
  <div class="formula__heading">Заголовок <em>акцент</em></div>
  <div class="formula__row">
    <div class="formula__step">
      <div class="formula__step-title">Компонент A</div>
      <div class="formula__step-text">Описание</div>
    </div>
    <div class="formula__arrow">+</div>
    <div class="formula__step">
      <div class="formula__step-title">Компонент B</div>
      <div class="formula__step-text">Описание</div>
    </div>
    <div class="formula__arrow">=</div>
    <div class="formula__result">
      <div class="formula__step-title">Результат</div>
      <div class="formula__step-text">Описание</div>
    </div>
  </div>
  <p class="formula__note">Курсивная пояснительная заметка внизу.</p>
</div>
```

---

## Полный CSS (копировать целиком)

```css
*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
:root { --accent: #6b4f35; --split: 60%; }

@page {
  size: 1280px 720px;
  margin: 0;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  background: #ffffff;
  color: #1a1a1a;
  font-size: 17px;
  line-height: 1.75;
  -webkit-font-smoothing: antialiased;
}

.slide {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  page-break-after: always;
  position: relative;
}

.divider {
  position: absolute;
  top: 0;
  bottom: 0;
  left: var(--split);
  width: 1px;
  background: #e5dccf;
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 48px;
  border-bottom: 1px solid #f0e9df;
  background: #fff;
  z-index: 10;
  flex-shrink: 0;
  width: var(--split);
}
.nav__logo { text-decoration: none; display: flex; align-items: center; }
.nav__logo img { height: 30px; width: auto; }
.nav__logo-name {
  font-family: 'DM Sans', sans-serif;
  font-size: 14px; font-weight: 400; font-style: italic;
  color: #948a7c; letter-spacing: 0.5px;
  margin-right: 8px;
}

.slide__body {
  flex: 1;
  display: flex;
  align-items: center;
  width: var(--split);
  padding: 0 48px;
}

.slide__inner {
  width: 100%;
  max-width: 580px;
}

/* ===== БАЗОВЫЕ ЭЛЕМЕНТЫ ===== */

.hero { padding: 0; }
.badge {
  display: inline-block; font-size: 11px; font-weight: 600;
  color: var(--accent); border: 1px solid var(--accent);
  padding: 5px 16px; margin-bottom: 20px;
  letter-spacing: 2px; text-transform: uppercase;
}
.hero h1 {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 36px; font-weight: 700; line-height: 1.25; margin-bottom: 16px;
}
.hero h1 em { font-style: italic; color: var(--accent); }
.hero__desc { font-size: 17px; color: #6b6157; line-height: 1.7; }
.hero__meta { font-size: 13px; color: #a39889; margin-top: 16px; letter-spacing: 1px; }

.section-heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3;
  padding: 0 0 20px;
}
.section-heading em { font-style: italic; color: var(--accent); }

.highlight { background: #f5f0e8; padding: 18px 22px; margin: 20px 0; font-size: 15px; line-height: 1.75; color: #4a4238; }

.sub-heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 20px; font-weight: 700; padding: 24px 0 10px;
}

.text { font-size: 16px; color: #4a4238; line-height: 1.75; margin-bottom: 14px; }

.guide-list { list-style: none; margin: 12px 0 20px; }
.guide-list li {
  font-size: 15px; line-height: 1.7; color: #4a4238;
  padding: 6px 0 6px 18px; position: relative;
  border-bottom: 1px solid #f0e9df;
}
.guide-list li:last-child { border-bottom: none; }
.guide-list li::before {
  content: ''; position: absolute; left: 0; top: 14px;
  width: 5px; height: 5px; border-radius: 50%; background: var(--accent);
}
.guide-list li strong { color: #1a1a1a; }

.scenario-card { border: 1px solid #e5dccf; padding: 24px; margin: 18px 0; background: #faf6f0; }
.scenario-card__num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 13px;
  color: var(--accent); letter-spacing: 1px; margin-bottom: 6px;
}
.scenario-card__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 18px; font-weight: 700; line-height: 1.4; margin-bottom: 16px;
}
.scenario-card__point { margin-bottom: 12px; }
.scenario-card__point-label { font-weight: 600; font-size: 15px; color: #1a1a1a; }
.scenario-card__point-text { font-size: 14px; color: #6b6157; line-height: 1.7; }
.scenario-card__tip {
  background: #f0e9df; padding: 12px 16px; margin-top: 14px;
  font-size: 13px; color: #5a5147; line-height: 1.65;
}
.scenario-card__tip strong { color: var(--accent); }

.footer-note {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 17px; font-style: italic; color: #4a4238;
  padding: 28px 0 0;
}
.footer-note em { color: var(--accent); }

/* ===== СХЕМКА 1: ЦИТАТА-АКЦЕНТ ===== */

.quote-slide__label {
  font-size: 11px; font-weight: 600; color: #a39889;
  letter-spacing: 2px; text-transform: uppercase; margin-bottom: 28px;
}
.quote-slide__mark {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 80px; color: var(--accent); line-height: 0.5;
  margin-bottom: 16px; opacity: 0.3;
}
.quote-slide__text {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 24px; font-weight: 400; font-style: italic;
  line-height: 1.5; color: #1a1a1a; max-width: 480px; margin-bottom: 28px;
}
.quote-slide__text em { color: var(--accent); }
.quote-slide__divider { width: 40px; height: 2px; background: var(--accent); margin-bottom: 20px; }
.quote-slide__source { font-size: 14px; color: #948a7c; line-height: 1.6; }

/* ===== СХЕМКА 2: ШАГИ С ЛИНИЕЙ ===== */

.steps__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 32px;
}
.steps__heading em { font-style: italic; color: var(--accent); }
.steps__list { position: relative; padding-left: 32px; }
.steps__list::before {
  content: ''; position: absolute; left: 7px; top: 8px; bottom: 8px;
  width: 1px; background: #e5dccf;
}
.steps__item { position: relative; padding-bottom: 24px; }
.steps__item:last-child { padding-bottom: 0; }
.steps__dot {
  position: absolute; left: -32px; top: 4px;
  width: 15px; height: 15px; border: 2px solid var(--accent);
  background: #fff; border-radius: 50%;
}
.steps__item--active .steps__dot { background: var(--accent); }
.steps__item-title { font-weight: 600; font-size: 16px; color: #1a1a1a; margin-bottom: 4px; }
.steps__item-text { font-size: 14px; color: #6b6157; line-height: 1.6; }

/* ===== СХЕМКА 3: НУМЕРОВАННЫЙ СПИСОК ===== */

.numlist__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 32px;
}
.numlist__heading em { font-style: italic; color: var(--accent); }
.numlist__item {
  display: flex; gap: 24px; align-items: baseline;
  padding: 16px 0; border-bottom: 1px solid #f0e9df;
}
.numlist__item:last-child { border-bottom: none; }
.numlist__num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-weight: 400;
  font-size: 36px; color: var(--accent); opacity: 0.25;
  min-width: 48px; text-align: right; line-height: 1; flex-shrink: 0;
}
.numlist__text { font-size: 15px; color: #1a1a1a; line-height: 1.6; }
.numlist__text strong { font-weight: 600; }
.numlist__text span { color: #6b6157; }

/* ===== СХЕМКА 4: АКЦЕНТНАЯ ПОЛОСА СЛЕВА ===== */

.accent-bar__label {
  font-size: 11px; font-weight: 600; color: #a39889;
  letter-spacing: 2px; text-transform: uppercase; margin-bottom: 24px;
}
.accent-bar__block { border-left: 3px solid var(--accent); padding-left: 28px; }
.accent-bar__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 26px; font-weight: 700; line-height: 1.35; margin-bottom: 16px;
}
.accent-bar__title em { font-style: italic; color: var(--accent); }
.accent-bar__text { font-size: 15px; color: #4a4238; line-height: 1.75; margin-bottom: 20px; }
.accent-bar__footer {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 15px; font-style: italic; color: #948a7c;
  padding-top: 16px; border-top: 1px solid #f0e9df;
}

/* ===== СХЕМКА 5: ЧЕК-ЛИСТ ===== */

.checklist__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 28px;
}
.checklist__heading em { font-style: italic; color: var(--accent); }
.checklist__grid { display: grid; grid-template-columns: 1fr 1fr; gap: 0; }
.checklist__col-label {
  font-size: 11px; font-weight: 600; letter-spacing: 1.5px;
  text-transform: uppercase; padding-bottom: 14px; margin-bottom: 10px;
  border-bottom: 1px solid #e5dccf;
}
.checklist__col-label--do { color: var(--accent); }
.checklist__col-label--dont { color: #a39889; }
.checklist__col:first-child { padding-right: 20px; border-right: 1px solid #f0e9df; }
.checklist__col:last-child { padding-left: 20px; }
.checklist__item {
  display: flex; gap: 10px; padding: 8px 0;
  font-size: 14px; color: #4a4238; line-height: 1.6; align-items: baseline;
}
.checklist__mark { flex-shrink: 0; font-size: 14px; font-weight: 700; width: 16px; }
.checklist__mark--do { color: var(--accent); }
.checklist__mark--dont { color: #cfc5b6; }

/* ===== СХЕМКА 6: ТРИ МЕТРИКИ ===== */

.metrics__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 32px;
}
.metrics__heading em { font-style: italic; color: var(--accent); }
.metrics__row { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 0; }
.metrics__item {
  text-align: center; padding: 24px 12px;
  border-right: 1px solid #f0e9df;
}
.metrics__item:last-child { border-right: none; }
.metrics__number {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-weight: 400;
  font-size: 48px; color: var(--accent); opacity: 0.25;
  line-height: 1; margin-bottom: 8px;
}
.metrics__label {
  font-size: 12px; color: #948a7c; text-transform: uppercase;
  letter-spacing: 1px; margin-bottom: 8px;
}
.metrics__desc { font-size: 13px; color: #6b6157; line-height: 1.5; }

/* ===== СХЕМКА 7: ВОПРОС-ОТВЕТ ===== */

.qa__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 28px;
}
.qa__heading em { font-style: italic; color: var(--accent); }
.qa__item { margin-bottom: 24px; }
.qa__question {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 17px; font-style: italic; color: var(--accent);
  margin-bottom: 8px; padding-left: 32px; position: relative;
}
.qa__question::before {
  content: '?'; position: absolute; left: 0; top: -4px;
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-weight: 400;
  font-size: 28px; color: var(--accent); opacity: 0.25;
}
.qa__answer {
  font-size: 15px; color: #4a4238; line-height: 1.7;
  padding-left: 32px; border-left: 1px solid #e5dccf;
}

/* ===== СХЕМКА 8: ФОРМУЛА ===== */

.formula__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 28px;
}
.formula__heading em { font-style: italic; color: var(--accent); }
.formula__row {
  display: flex; align-items: center; gap: 16px; margin-bottom: 32px;
}
.formula__step {
  flex: 1; background: #f5f0e8; padding: 18px 16px; text-align: center;
}
.formula__step-title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 15px; font-weight: 700; margin-bottom: 4px;
}
.formula__step-text { font-size: 12px; color: #6b6157; line-height: 1.5; }
.formula__arrow { color: var(--accent); font-size: 18px; flex-shrink: 0; opacity: 0.4; }
.formula__result {
  border: 1px solid var(--accent); padding: 18px 16px; text-align: center; flex: 1;
}
.formula__result .formula__step-title { color: var(--accent); }
.formula__note { font-size: 14px; color: #948a7c; font-style: italic; margin-top: 8px; }

/* ===== АДАПТИВ ===== */

@media print {
  html, body { width: 1280px; }
  .slide {
    width: 1280px; height: 720px;
    page-break-after: always; page-break-inside: avoid;
  }
  .slide:last-child { page-break-after: auto; }
  body { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
}

/* ВАЖНО: только screen — иначе правило течёт в print/PDF и ломает 60/40 split (навбар на всю ширину, исчезает разделитель и правая зона под видео) */
@media screen and (max-width: 768px) {
  .nav { padding: 16px 20px; width: 100%; }
  .hero h1 { font-size: 26px; }
  .section-heading { font-size: 22px; }
  .slide__body { width: 100%; padding: 0 20px; }
  .divider { display: none; }
}
```

## Шаблон HTML-слайда

```html
<!-- Титульный слайд -->
<div class="slide">
<div class="divider"></div>
<nav class="nav">
  <a class="nav__logo" href="#"><img src="https://maiyamaiya19999-bit.github.io/maysoulme-assets/logo-ms.png" alt="MS"></a>
  <span class="nav__logo-name">maysoulme</span>
</nav>
<div class="slide__body">
  <div class="slide__inner">
    <div class="hero">
      <div class="badge">УРОК</div>
      <h1>Заголовок <em>акцентная часть</em></h1>
      <p class="hero__desc">Описание презентации</p>
      <p class="hero__meta">Тег 1 &middot; Тег 2 &middot; Тег 3</p>
    </div>
  </div>
</div>
</div>

<!-- Контентный слайд -->
<div class="slide">
<div class="divider"></div>
<nav class="nav">
  <a class="nav__logo" href="#"><img src="https://maiyamaiya19999-bit.github.io/maysoulme-assets/logo-ms.png" alt="MS"></a>
  <span class="nav__logo-name">maysoulme</span>
</nav>
<div class="slide__body">
  <div class="slide__inner">
    <h2 class="section-heading">Заголовок <em>акцент</em></h2>
    <p class="text">Текст слайда.</p>
  </div>
</div>
</div>
```

## Как использовать

1. Получи текст/тему от пользователя
2. Разбей на логические слайды (один экран = одна мысль)
3. Первый слайд — титульный с бейджем, заголовком, описанием
4. Остальные слайды — чередуй базовые и схемки:
   - **Цитата** — для ключевых мыслей и выводов
   - **Шаги** — для процессов и последовательностей
   - **Нумерованный список** — для структур и анатомий
   - **Акцентная полоса** — для главных правил и принципов
   - **Чек-лист** — для сравнений (делай / не делай)
   - **Метрики** — для цифр и статистики
   - **Вопрос-ответ** — для FAQ и разбора сомнений
   - **Формула** — для визуальных уравнений (A + B = C)
5. Каждый 2–3-й слайд должен быть схемкой — так интереснее смотреть
6. Не перегружай слайд — контент должен поместиться в 60% экрана по центру
7. Сохрани как `index.html` в папку проекта

## Экспорт в PDF

Генерировать строго с размером страницы 1280×720px (16:9), иначе вёрстка ломается:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu \
  --no-pdf-header-footer --print-to-pdf="presentation.pdf" --no-margins \
  --paper-width=13.333 --paper-height=7.5 "file://$(pwd)/index.html"
```

(13.333×7.5 дюйма = 1280×720px при 96dpi.)

**ОБЯЗАТЕЛЬНО проверить сам PDF в print-режиме, а не скриншот экрана** (на экране баг не виден):

```bash
sips -s format png presentation.pdf --out _check.png   # стр. 1
```

Посмотреть глазами: есть ли вертикальный разделитель на 60%, пустые ли правые 40% под видео, стоит ли *maysoulme* у разделителя (а не у правого края). После проверки удалить `_check.png`.
