

# Git Commands Reference

## Основные команды
Документация RS School: https://rs.school/ru/docs/git-convention
https://github.com/rolling-scopes-school/tasks/blob/master/tasks/cv/git.md


### Инициализация и клонирование
```bash
# Инициализировать новый репозиторий
git init

# Клонировать существующий репозиторий
git clone <url>
git clone <url> <directory-name>
```

### Проверка статуса и истории
```bash
# Проверить статус файлов
git status

# Посмотреть историю коммитов
git log
git log --oneline
git log --graph --oneline --all
```

### Работа с изменениями
```bash
# Добавить файлы в staging area
git add <file>
git add .
git add -A

# Создать коммит
git commit -m "Сообщение коммита"
git commit -am "Добавить и закоммитить измененные файлы"

# Отменить изменения
git restore <file>
git restore --staged <file>
```

## Пример работы с проектом RS School CV

### Структура веток для проекта

```
main (или master)
  ├── gh-pages (для Markdown CV)
  └── rsschool-cv-html (для HTML/CSS/JS CV)
```

### Шаг 1: Создание ветки gh-pages для Markdown CV

```bash
# Переключиться на main ветку
git checkout main

# Создать и переключиться на ветку gh-pages
git checkout -b gh-pages

# Создать файл cv.md
touch cv.md

# Добавить контент в cv.md (через редактор)
# Например: имя, контакты, навыки, образование

# Добавить файлы
git add cv.md

# Создать коммит
git commit -m "docs: add cv.md with personal information"

# Отправить ветку на GitHub
git push -u origin gh-pages
```

### Шаг 2: Создание README.md с ссылкой

```bash
# Находясь на ветке gh-pages
touch README.md

# Добавить ссылку на CV в README.md
# https://GITHUB-USERNAME.github.io/rsschool-cv/cv

git add README.md
git add -A
git commit -m "docs: add link to cv.md in README"
git push origin gh-pages
```

### Шаг 3: Создание ветки rsschool-cv-html

```bash
# Переключиться обратно на gh-pages
git checkout gh-pages

# Создать новую ветку для HTML/CSS версии
git checkout -b rsschool-cv-html

# Создать файлы проекта
touch index.html style.css

# Добавить базовую структуру HTML
git add index.html
git commit -m "init: add basic HTML structure"

# Добавить стили
git add style.css
git commit -m "feat: add basic styles for CV"

# Отправить ветку на GitHub
git push -u origin rsschool-cv-html
```

### Примеры коммитов для CV проекта

#### Инициализация и структура

```bash
# Создание базовых файлов
git commit -m "init: create project structure"
git commit -m "init: add index.html and style.css"

# Настройка конфигурации
git commit -m "chore: add .gitignore"
git commit -m "docs: create README.md with project description"
```

#### Добавление секций CV (Markdown версия)

```bash
git commit -m "docs: add contact information to cv.md"
git commit -m "docs: add summary section"
git commit -m "docs: add skills section with technologies"
git commit -m "docs: add code examples section"
git commit -m "docs: add work experience"
git commit -m "docs: add education information"
git commit -m "docs: add English language level"
```

#### Добавление секций CV (HTML/CSS версия)

```bash
# HTML структура
git commit -m "feat: add header with navigation"
git commit -m "feat: add hero section with photo and intro"
git commit -m "feat: add contacts section"
git commit -m "feat: add about me section"
git commit -m "feat: add skills section with icons"
git commit -m "feat: add code examples with syntax highlighting"
git commit -m "feat: add projects section"
git commit -m "feat: add experience timeline"
git commit -m "feat: add education section"
git commit -m "feat: add footer with social links"

# CSS стили
git commit -m "style: add CSS reset and variables"
git commit -m "style: implement responsive grid layout"
git commit -m "style: add typography and color scheme"
git commit -m "style: style header and navigation"
git commit -m "style: style hero section"
git commit -m "style: add animations for skills section"
git commit -m "style: implement mobile-first responsive design"
git commit -m "style: add dark theme support"

# JavaScript функциональность
git commit -m "feat: add smooth scroll navigation"
git commit -m "feat: implement theme toggle"
git commit -m "feat: add mobile menu functionality"
git commit -m "feat: add form validation"
```

#### Улучшения и исправления

```bash
# Оптимизация
git commit -m "perf: optimize images for web"
git commit -m "perf: minify CSS and JS files"
git commit -m "perf: add lazy loading for images"

# Исправления
git commit -m "fix: correct layout issues on mobile devices"
git commit -m "fix: resolve navigation menu overlapping content"
git commit -m "fix: fix typos in content"
git commit -m "fix: correct broken links"

# Доступность
git commit -m "feat: add aria labels for accessibility"
git commit -m "feat: improve keyboard navigation"
git commit -m "feat: add alt text to images"
```

### Шаг 4: Pull Request и слияние веток

```bash
# После создания Pull Request на GitHub и его одобрения
# Переключиться на целевую ветку
git checkout gh-pages

# Получить последние изменения
git pull origin gh-pages

# Слить ветку rsschool-cv-html
git merge rsschool-cv-html

# Или использовать rebase для чистой истории
git rebase rsschool-cv-html

# Отправить изменения
git push origin gh-pages
```

### Шаг 5: Обновление README.md в ветке rsschool-cv-html

```bash
# Находясь на ветке rsschool-cv-html
git checkout rsschool-cv-html

# Обновить README.md со ссылкой на HTML версию
# https://GITHUB-USERNAME.github.io/rsschool-cv/

git add README.md
git commit -m "docs: update README with link to HTML CV"
git push origin rsschool-cv-html
```

### Работа с Pull Requests

```bash
# Создать Pull Request через GitHub UI:
# rsschool-cv-html → gh-pages

# Типичное описание PR:
# Title: feat: add HTML/CSS version of CV
# Description:
# - Added responsive HTML layout
# - Implemented CSS styling with mobile-first approach
# - Added smooth animations and transitions
# - Included all required sections: contacts, skills, code examples, etc.

# После ревью и одобрения - merge через GitHub UI
# Затем обновить локальную ветку:
git checkout gh-pages
git pull origin gh-pages
```

### Синхронизация с удаленным репозиторием

```bash
# Проверить удаленные ветки
git branch -r

# Получить все изменения из удаленного репозитория
git fetch origin

# Обновить текущую ветку
git pull origin <branch-name>

# Отправить все ветки
git push origin --all

# Удалить локальную ветку после merge
git branch -d rsschool-cv-html

# Удалить удаленную ветку (если нужно)
git push origin --delete rsschool-cv-html
```

### Типичный workflow для задания

```bash
# 1. Клонировать репозиторий
git clone https://github.com/username/rsschool-cv.git
cd rsschool-cv

# 2. Создать ветку gh-pages для Markdown CV
git checkout -b gh-pages
# ... работа над cv.md ...
git add cv.md README.md
git commit -m "docs: create Markdown CV"
git push -u origin gh-pages

# 3. Создать Pull Request: gh-pages → gh-pages (self-review)

# 4. Создать ветку для HTML версии
git checkout -b rsschool-cv-html
# ... работа над index.html, style.css ...
git add .
git commit -m "feat: implement HTML/CSS CV"
git push -u origin rsschool-cv-html

# 5. Создать Pull Request: rsschool-cv-html → gh-pages

# 6. После review - merge через GitHub

# 7. Обновить локальную gh-pages
git checkout gh-pages
git pull origin gh-pages

# 8. Проверить результат на GitHub Pages
# https://username.github.io/rsschool-cv/
```

### Работа с конфликтами

```bash
# Если возникли конфликты при merge
git merge rsschool-cv-html
# CONFLICT (content): Merge conflict in README.md

# Разрешить конфликты вручную в файлах
# Затем:
git add README.md
git commit -m "merge: resolve conflicts with rsschool-cv-html"
git push origin gh-pages


git add -A


feat	    новая функциональность
fix	      исправление ошибки
docs	    изменения в документации
style	    форматирование кода (не влияющее на логику)
refactor	улучшение кода без изменения поведения
perf	    оптимизация производительности
test	    добавление или правка тестов
chore	    прочие задачи (например, обновление зависимостей)

