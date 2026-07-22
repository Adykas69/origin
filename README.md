# Общий конспект по Git, GitHub и Markdown
 

---

# 1. Git и GitHub

## Git

**Git** — система контроля версий.

Позволяет:

* сохранять историю изменений;
* возвращаться к старым версиям;
* работать с ветками;
* объединять изменения;
* работать над проектом в команде.

## GitHub

**GitHub** — сайт для хранения Git-репозиториев в интернете.

```text
Git → управляет версиями проекта
GitHub → хранит проект онлайн
```

## Основные понятия

| Понятие               | Значение                               |
| --------------------- | -------------------------------------- |
| Репозиторий           | Папка проекта под управлением Git      |
| Коммит                | Сохранённая версия проекта             |
| Ветка                 | Отдельная линия разработки             |
| Локальный репозиторий | Проект на компьютере                   |
| Удалённый репозиторий | Проект на GitHub                       |
| `origin`              | Стандартное имя удалённого репозитория |
| `main`                | Главная ветка                          |
| HEAD                  | Текущее положение в Git                |

---

# 2. Установка Git

Скачать Git:

```text
git-scm.com
```

Во время установки:

```text
Папка — оставить по умолчанию
Компоненты — оставить по умолчанию
Редактор — Visual Studio Code
Главная ветка — main
Остальные настройки — Next
```

Проверить установку:

```bash
git --version
```

Успешный результат:

```text
git version 2.x.x
```

Если команда не работает:

1. Закрыть и открыть терминал.
2. Перезапустить VS Code.
3. Перезагрузить компьютер.
4. Проверить `PATH` или `git.path`. 

---

# 3. Настройка Git в VS Code

Открыть настройки:

```text
File → Preferences → Settings
```

или:

```text
Ctrl + ,
```

Найти:

```text
Git: Path
```

При необходимости указать в `settings.json`:

```json
{
  "git.path": "C:/Program Files/Git/cmd/git.exe"
}
```

Проверить:

```bash
git --version
```

---

# 4. Настройка автора коммитов

Указать имя и почту для всех проектов:

```bash
git config --global user.name "Shuhrat"
git config --global user.email "example@email.com"
```

Проверить:

```bash
git config --list
```

Настройки только для текущего проекта:

```bash
git config user.name "Project User"
git config user.email "project@example.com"
```

```text
--global → для всех проектов
без --global → только для текущего проекта
```

---

# 5. Создание локального репозитория

Перейти в папку проекта:

```bash
cd путь-к-проекту
```

Создать Git-репозиторий:

```bash
git init
```

После этого появляется скрытая папка:

```text
.git
```

Она хранит:

* коммиты;
* ветки;
* историю;
* настройки репозитория.

```text
Обычная папка + git init = локальный репозиторий
```

`git init` не загружает проект на GitHub.

---

# 6. Основной рабочий цикл Git

## Проверить состояние

```bash
git status
```

Краткий вариант:

```bash
git status -s
```

## Добавить изменения в Stage

Один файл:

```bash
git add index.html
```

Все файлы:

```bash
git add .
```

## Создать коммит

```bash
git commit -m "Описание изменений"
```

Хорошие сообщения:

```text
Add navigation menu
Fix login form
Update README
Remove unused styles
```

## Отправить изменения

```bash
git push
```

## Главная схема

```text
Изменить файлы
↓
git status
↓
git add .
↓
git commit -m "Описание"
↓
git push
```

---

# 7. Состояния файлов

| Обозначение | Значение                   |
| ----------- | -------------------------- |
| `M`         | Файл изменён               |
| `A`         | Файл добавлен              |
| `D`         | Файл удалён                |
| `R`         | Файл переименован          |
| `??`        | Новый неотслеживаемый файл |

```text
 M index.html
```

Файл изменён, но не добавлен в Stage.

```text
M  index.html
```

Файл уже находится в Stage.

```text
MM index.html
```

Файл добавили в Stage, а затем снова изменили.

---

# 8. Создание репозитория на GitHub

На GitHub:

```text
New repository
↓
Repository name
↓
Public или Private
↓
Create repository
```

Для пустого удалённого репозитория можно не добавлять:

* README;
* `.gitignore`;
* License.

---

# 9. Первая загрузка проекта на GitHub

```bash
git add .
git commit -m "First commit"
git branch -M main
git remote add origin URL
git push -u origin main
```

Что делают команды:

| Команда                     | Назначение                   |
| --------------------------- | ---------------------------- |
| `git add .`                 | Подготовить изменения        |
| `git commit`                | Создать коммит               |
| `git branch -M main`        | Назвать главную ветку `main` |
| `git remote add origin URL` | Подключить GitHub            |
| `git push -u origin main`   | Первая отправка              |

После первой отправки:

```bash
git add .
git commit -m "Описание"
git push
```

Проверить подключение:

```bash
git remote -v
```

---

# 10. Source Control в VS Code

Открыть:

```text
Ctrl + Shift + G
```

| VS Code               | Команда Git             |
| --------------------- | ----------------------- |
| Initialize Repository | `git init`              |
| `+` возле файла       | `git add файл`          |
| `+` возле Changes     | `git add .`             |
| Commit                | `git commit`            |
| Publish Branch        | Первая публикация       |
| Push                  | `git push`              |
| Pull                  | `git pull`              |
| Sync Changes          | `git pull` + `git push` |
| Discard Changes       | Отменить изменения      |

Первый проект:

```text
Initialize Repository
↓
Добавить файлы
↓
Commit
↓
Publish Branch
```

Обычная работа:

```text
Изменить файл
↓
Stage
↓
Commit
↓
Push
```

---

# 11. Клонирование репозитория

Скачать только файлы:

```text
Code → Download ZIP
```

ZIP не содержит историю Git.

Получить полную копию:

```bash
git clone URL
```

После клонирования:

```bash
git status
git remote -v
```

## Push и Pull

```text
git push
Компьютер → GitHub
```

```text
git pull
GitHub → компьютер
```

Перед началом работы желательно:

```bash
git pull
```

---

# 12. История коммитов

Подробная история:

```bash
git log
```

Краткая:

```bash
git log --oneline
```

История с ветками:

```bash
git log --oneline --graph --all --decorate
```

Каждый коммит имеет уникальный код:

```text
a74c921
```

Это **хеш коммита**.

---

# 13. Git Graph

**Git Graph** — расширение VS Code для графического просмотра истории Git.

Установка:

```text
Extensions
↓
Git Graph
↓
Install
```

Открыть:

```text
Source Control → View Git Graph
```

или:

```text
Ctrl + Shift + P
Git Graph: View Git Graph
```

Показывает:

* коммиты;
* ветки;
* автора;
* дату;
* хеш;
* изменения файлов;
* положение HEAD.



---

# 14. Алиасы

**Алиас** — сокращение команды Git.

Создать:

```bash
git config --global alias.s "status --short"
git config --global alias.l "log --oneline"
git config --global alias.lg "log --oneline --graph --all --decorate"
git config --global alias.br "branch"
git config --global alias.co "checkout"
```

Использование:

```bash
git s
git l
git lg
git br
git co main
```

Показать алиасы:

```bash
git config --global --get-regexp alias
```

Удалить:

```bash
git config --global --unset alias.s
```

---

# 15. Отмена изменений

## Отменить изменения файла

Современная команда:

```bash
git restore index.html
```

Все файлы:

```bash
git restore .
```

Старый вариант:

```bash
git checkout -- index.html
git checkout -- .
```

⚠️ Незакоммиченные изменения будут удалены.

## Убрать файл из Stage

```bash
git restore --staged index.html
```

Все файлы:

```bash
git restore --staged .
```

Старый вариант:

```bash
git reset index.html
git reset .
```

Изменения останутся в файлах.

## Удалить последний коммит, сохранив изменения

```bash
git reset --soft HEAD~1
```

Изменения останутся в Stage.

## Удалить коммит и изменения

```bash
git reset --hard HEAD~1
```

⚠️ Изменения будут удалены.

```text
HEAD → текущий коммит
HEAD~1 → предыдущий коммит
HEAD~2 → два коммита назад
```

---

# 16. Переход к старому коммиту

Посмотреть хеши:

```bash
git log --oneline
```

Перейти:

```bash
git checkout HASH
```

Возникает состояние:

```text
detached HEAD
```

Чтобы вернуться:

```bash
git switch main
```

Чтобы продолжить работу от старого коммита:

```bash
git switch -c new-branch
```

---

# 17. Работа с ветками

**Ветка** — отдельная линия разработки.

```text
main → стабильная версия
develop → разработка
feature-menu → новая функция
bugfix-login → исправление ошибки
```

## Посмотреть ветки

```bash
git branch
```

С последними коммитами:

```bash
git branch -v
```

`*` показывает текущую ветку.

## Создать ветку

```bash
git branch develop
```

Команда создаёт ветку, но не переключает на неё.

## Перейти на ветку

```bash
git switch develop
```

Старый вариант:

```bash
git checkout develop
```

## Создать и сразу перейти

```bash
git switch -c develop
```

Старый вариант:

```bash
git checkout -b develop
```

---

# 18. Переименование и удаление веток

Переименовать текущую ветку:

```bash
git branch -m новое-имя
```

Принудительно:

```bash
git branch -M main
```

Удалить безопасно:

```bash
git branch -d develop
```

Удалить принудительно:

```bash
git branch -D develop
```

Нельзя удалить текущую ветку:

```bash
git switch main
git branch -d develop
```

---

# 19. Публикация ветки

Первая публикация:

```bash
git push -u origin develop
```

Создаётся связь:

```text
develop ↔ origin/develop
```

Следующие отправки:

```bash
git push
```

Удалить ветку на GitHub:

```bash
git push origin --delete develop
```

Обновить список удалённых веток:

```bash
git fetch --prune
```

---

# 20. Слияние веток

**Merge** — объединение изменений веток.

Главное правило:

> Сначала перейти в ветку, в которую нужно добавить изменения.

Добавить `fix` в `main`:

```bash
git switch main
git merge fix
```

## Fast-forward

Происходит, если после создания `fix` ветка `main` не менялась.

Git просто перемещает указатель вперёд.

Merge-коммит обычно не создаётся.

## Обычное слияние

Если обе ветки менялись, Git объединяет их и создаёт merge-коммит.

---

# 21. Конфликты слияния

Конфликт возникает, когда две ветки изменили одну часть файла.

Маркеры:

```text
<<<<<<< HEAD
текущая версия
=======
входящая версия
>>>>>>> fix
```

В VS Code:

| Кнопка          | Действие                 |
| --------------- | ------------------------ |
| Accept Current  | Оставить текущую версию  |
| Accept Incoming | Оставить входящую версию |
| Accept Both     | Оставить обе             |
| Compare         | Сравнить                 |

После исправления:

```bash
git add .
git commit
```

Отменить незавершённое слияние:

```bash
git merge --abort
```

После успешного слияния:

```bash
git branch -d fix
```



---

# 22. `.gitignore`

**`.gitignore`** — файл со списком файлов, которые Git не должен отслеживать.

Пример:

```gitignore
node_modules/
.env
*.log
dist/
build/
.vscode/
.idea/
```

## Правила

Файл:

```gitignore
debug.log
```

Папка:

```gitignore
cache/
```

Все файлы типа:

```gitignore
*.log
```

Вернуть один файл:

```gitignore
*.log
!important.log
```

Комментарий:

```gitignore
# Секретные данные
.env
```

## Node.js

```text
Сохранять:
package.json
package-lock.json

Не сохранять:
node_modules/
```

Зависимости восстанавливаются:

```bash
npm install
```

## Если файл уже отслеживается

Файл:

```bash
git rm --cached .env
```

Папка:

```bash
git rm -r --cached node_modules
```

Проверить правило:

```bash
git check-ignore -v путь-к-файлу
```

Сам `.gitignore` нужно добавить в коммит.

---

# 23. Markdown

**Markdown** — простой язык оформления текста.

Файлы:

```text
README.md
notes.md
instructions.md
```

Расширение:

```text
.md
```

## README.md

**README.md** — основной файл с описанием проекта.

GitHub автоматически показывает его на странице репозитория.

Обычно содержит:

```markdown
# Название проекта

## Описание

## Технологии

## Установка

## Использование

## Автор
```

---

# 24. Основной синтаксис Markdown

## Заголовки

```markdown
# Заголовок 1
## Заголовок 2
### Заголовок 3
```

## Списки

```markdown
- Пункт
- Пункт
```

```markdown
1. Пункт
2. Пункт
```

## Форматирование

```markdown
*Курсив*

**Жирный**

***Жирный курсив***

~~Зачёркнутый~~
```

## Код

```markdown
`git status`
```

````markdown
```bash
git status
git add .
```
````

## Цитата

```markdown
> Текст цитаты
```

## Ссылка

```markdown
[GitHub](https://github.com)
```

## Изображение

```markdown
![Описание](images/photo.jpg)
```

## Таблица

```markdown
| Команда | Описание |
|---------|----------|
| git add | Добавить |
```

## Чек-лист

```markdown
- [x] Выполнено
- [ ] Не выполнено
```

## Preview в VS Code

```text
Ctrl + Shift + V
```

Открыть сбоку:

```text
Ctrl + K, затем V
```

---

# 25. Settings Sync в VS Code

**Settings Sync** синхронизирует:

* настройки;
* расширения;
* горячие клавиши;
* темы;
* сниппеты;
* профили.

Включить:

```text
Accounts
↓
Settings Sync
↓
Sign in
↓
Sign in with GitHub
```

На новом компьютере войти в тот же аккаунт.

Отключить:

```text
Accounts → Turn Off Settings Sync
```

```text
Settings Sync → настройки VS Code
GitHub-репозиторий → файлы проекта
```

---

# 26. GitHub Gist

**Gist** — сервис для небольших фрагментов кода и текста.

Подходит для:

* шаблонов;
* функций;
* команд;
* конфигураций;
* заметок.

```text
Gist → маленький фрагмент
Repository → полноценный проект
```

Создать:

```text
Your gists
↓
New gist
↓
Описание
↓
Имя файла
↓
Create public/secret gist
```

**Public** — доступен всем.

**Secret** — доступен по ссылке, но не является полностью приватным.

Нельзя хранить:

* пароли;
* токены;
* API-ключи;
* `.env`;
* SSH-ключи.

Основные команды расширения VS Code:

```text
Gist: Create New Gist
Gist: Open Gist
Gist: Insert Text From Gist File
Gist: Delete Gist
```



---

# 27. GitHub Pages

**GitHub Pages** — бесплатный хостинг статических сайтов.

Поддерживает:

* HTML;
* CSS;
* JavaScript;
* изображения.

Не поддерживает серверный:

* PHP;
* Node.js;
* Python;
* базы данных.

Главный файл:

```text
index.html
```

Структура:

```text
project/
├── index.html
├── style.css
├── script.js
└── images/
```

Использовать относительные пути:

```html
<link rel="stylesheet" href="style.css">
<script src="script.js"></script>
<img src="images/photo.jpg">
```

Включить:

```text
Settings
↓
Pages
↓
Deploy from a branch
↓
main
↓
/(root)
↓
Save
```

Адрес:

```text
https://username.github.io/project-name/
```

Обновление сайта:

```bash
git add .
git commit -m "Update website"
git push
```

---

# 28. Оформление профиля GitHub

Заполнить:

```text
Name
Bio
Location
Website
Avatar
```

Пример Bio:

```text
Junior Frontend Developer | HTML • CSS • JavaScript
```

## Profile README

Создать публичный репозиторий, название которого совпадает с логином:

```text
Логин: Shuhrat-dev
Репозиторий: Shuhrat-dev
```

Внутри должен быть:

```text
README.md
```

Структура:

```markdown
# Привет! Я Шухрат

## Обо мне

## Технологии

## Лучшие проекты

## Сейчас изучаю

## Контакты
```

Закрепить проекты:

```text
Customize your pins
```

Лучше несколько качественных проектов, чем много статистики и значков.

---

# 29. Fork и Pull Request

## Fork

**Fork** — копия чужого репозитория в вашем аккаунте.

Не изменяет оригинальный проект.

Создать:

```text
Fork → Create fork
```

Клонировать свой Fork:

```bash
git clone https://github.com/your-name/project.git
```

## Origin и upstream

```text
origin → ваш Fork
upstream → оригинальный репозиторий
```

Добавить оригинал:

```bash
git remote add upstream https://github.com/author/project.git
```

## Рабочий процесс

```bash
git switch -c fix-name
git status
git add .
git commit -m "Fix issue"
git push -u origin fix-name
```

На GitHub:

```text
Compare & pull request
↓
Create pull request
```

**Pull Request** — предложение добавить изменения в оригинальный проект.

Если попросили исправления:

```bash
git add .
git commit -m "Address review comments"
git push
```

Новый PR создавать не нужно.

## Обновление Fork

```bash
git switch main
git fetch upstream
git merge upstream/main
git push origin main
```

---

# Главная шпаргалка

## Новый проект

```bash
git init
git status
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin URL
git push -u origin main
```

## Обычная работа

```bash
git pull
git status
git add .
git commit -m "Описание изменений"
git push
```

## Ветки

```bash
git branch
git switch -c feature-name
git switch main
git merge feature-name
git branch -d feature-name
```

## История

```bash
git log
git log --oneline
git log --oneline --graph --all --decorate
```

## Отмена

```bash
git restore файл
git restore --staged файл
git reset --soft HEAD~1
git reset --hard HEAD~1
```

## Удалённый репозиторий

```bash
git remote add origin URL
git remote -v
git push -u origin main
git push
git pull
git clone URL
```

## Слияние

```bash
git switch main
git merge feature-name
git add .
git commit
git merge --abort
```

## Удаление веток

```bash
git branch -d feature-name
git push origin --delete feature-name
git fetch --prune
```

---

# Самое главное

```text
Изменить файлы
↓
git status
↓
git add .
↓
git commit -m "Описание"
↓
git push
```

Для новой задачи:

```text
git switch -c новая-ветка
↓
Работа
↓
Commit
↓
Push
↓
Merge или Pull Request
```

Основные команды, которые нужно знать:

```bash
git init
git status
git add .
git commit -m "..."
git log --oneline

git switch -c feature-name
git switch main
git merge feature-name

git remote add origin URL
git push -u origin main
git push
git pull
git clone URL

git restore файл
git restore --staged файл
git branch -d feature-name
```
