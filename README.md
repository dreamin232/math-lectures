# Конспекты лекций по математическому анализу

> Сайт с лекциями для студентов 1–2 курса. Собран на [Quarto](https://quarto.org).

## Структура проекта

```
math-lectures/
├── _quarto.yml              # Главный конфиг сайта
├── index.qmd                # Главная страница
├── references.bib           # Библиография (опционально)
├── lectures/
│   ├── 01-limits.qmd        # Пределы и непрерывность
│   ├── 02-derivatives.qmd   # Производные
│   ├── 03-integrals.qmd     # Интегралы
│   └── 04-multiple-integrals.qmd
├── assets/
│   ├── css/
│   │   ├── main.css
│   │   ├── custom-light.scss
│   │   └── custom-dark.scss
│   └── latex-preamble.tex
└── .github/workflows/
    └── deploy.yml           # Автодеплой на GitHub Pages
```

## Локальная разработка

```bash
# Превью с живым обновлением при сохранении файла
quarto preview

# Полная сборка сайта в папку docs/
quarto render

# Сборка только одной лекции
quarto render lectures/01-limits.qmd

# Сборка PDF одной лекции
quarto render lectures/01-limits.qmd --to pdf
```

## Публикация

### Первый раз (настройка)

1. Создайте репозиторий на GitHub
2. Выполните:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/math-lectures.git
   git push -u origin main
   ```
3. В GitHub: Settings → Pages → Source: **GitHub Actions**

После этого каждый `git push` в ветку `main` запускает сборку автоматически.

### Обычная работа

```bash
# Внесли правки в лекцию — публикуем
git add lectures/01-limits.qmd
git commit -m "Добавил доказательство теоремы о сжатой переменной"
git push
```
Через ~2 минуты сайт обновится на `https://YOUR_USERNAME.github.io/math-lectures/`.

## Как добавить новую лекцию

1. Создайте файл `lectures/05-series.qmd` по образцу существующих.
2. Добавьте его в `_quarto.yml` в секцию `sidebar.contents` и `navbar.menu`.
3. `git push` — сайт пересоберётся автоматически.

## Соглашения

- Формулы нумеруются через `{#eq-name}` и цитируются через `@eq-name`.
- Теоремы — через `{#thm-name}`, определения — `{#def-name}`.
- Доказательства всегда в `callout-tip` с `collapse: true`.
- Задачи — в `callout-warning`, ответы — в `callout-note` с `collapse: true`.
