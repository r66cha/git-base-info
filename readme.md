# Git — Базовые команды

## 1. Создание и клонирование репозитория

```bash
git init          # инициализация нового репозитория в текущей папке
git clone <url>   # клонировать удалённый репозиторий
```

## 2. Настройки Git

```bash
git config --global user.name "Name".     # Задает имя
git config --global user.email "Email".   # Задает почту
git config --list                         # Показать все настройки Git
git config --global --list                # Показать глобальные настройки Git
git config --global --edit                # Показать глобальные настройки Git через vim
```

## 3. Основные операции с файлами

```bash
git status           # Показать текущее состояние (изменения, staged/untracked)
git add <file>       # Добавить файл в индекс
git add .            # Добавить все изменения
git rm <file>        # Удалить файл из репозитория
git mv <old> <new>   # Переименовать/переместить файл
```

## 4. Коммиты (Commits)

```bash
git commit -m "сообщение"      # Создать коммит
git commit -am "сообщение"     # Добавить и закоммитить отслеживаемые файлы
```

## 5. История

```bash
git log             # История коммитов
git log --oneline   # Краткая история
git diff            # Показать изменения в рабочей директории
git show <commit>   # Показать детали конкретного коммита
```

## 6. Ветки

```bash
git branch                      # Список веток
git branch <name>               # Создать ветку featur/new_feature
git checkout <commit_hash>      # Переключиться на коммит (без изменения истории ветки)
git checkout <branch_name>      # Переключиться на ветку
git checkout -b <branch_name>   # Создать и переключиться на ветку
git checkout <file_name>        # Откат изменений в файле
git merge <branch_name>         # Слить ветку с текущей
git branch -d <branch_name>     # Удалить ветку
git switch <branch_name>        # Переключиться только на ветку *новая команда
```

## 7. Работа с удалённым репозиторием

```bash
git remote -v                 # Список удаленных репозиториев
git remote add origin <url>   # Добавить удалённый репозиторий
git push -u origin main       # Отправить ветку main в origin (Первый пуш)
git push                      # Отправить изменения           (Дальше можно так)
git pull                      # Получить изменения и объединить
git fetch                     # Скачать изменения без объединения

```

## 8. Сброс и отмена

```bash
git checkout -- <file>             # Отменить изменения в файле
git reset HEAD <file>              # Убрать файл из индекса
git reset --soft <commit_hash>     # Откат к коммиту (сохраняя изменения)
git reset --hard <commit_hash>     # Откат к коммиту без сохранения
git revert <commit_hash>           # Отменяющий коммит другого коммита
git restore <file_name>            # Отменяет несохранённые изменения в файле, откатывает на момент последнего коммита
git restore --staged <file_name>   # Убирает файл из staged, оставляя изменения
git restore .                      # Отменяет изменения всех файлов
git restore --source <commit>      # Восстанавливает файл из конкретного коммита
git restore --source HEAD~1 <file_name>   # Откат на 1 коммит назад у конкретного файла
```

## 9. Информация Git

```bash
git --version   # Версия Git
```

## 10. stash

**git stash** — это команда Git, которая временно сохраняет изменения в рабочем каталоге и индексе (staged и unstaged), убирая их из текущего состояния, чтобы мы могли переключиться на другую ветку или сделать pull без конфликтов.

```bash
# -- Сохранение изменений во временное хранилище
git stash              # Сохранить все изменения (staged + unstaged)
git stash -u           # Сохранить изменения + неотслеживаемые файлы (untracked)
git stash -a           # Сохранить всё, включая игнорируемые файлы
git stash save "msg"   # Сохранить изменения с комментарием

# -- Просмотр списка stash
git stash list      # Список всех stash
git stash show      # Показать изменения последнего stash (кратко)
git stash show -p   # Показать diff последнего stash

# -- Применение stash
git stash apply             # Применить последний stash (оставив его в списке)
git stash apply stash@{2}   # Применить конкретный stash по индексу
git stash pop               # Применить и удалить последний stash

# -- Управление stash
git stash drop stash@{0} # Удалить конкретный stash
git stash clear          # Удалить все stash
```

## 11. Оптимизация maintenance

**git maintenance** — это встроенный механизм Git для обслуживания и оптимизации репозитория. Он помогает поддерживать репозиторий в хорошем состоянии, особенно если он большой или активно используется.

```bash
git maintenance start    # Запускает автоматическое обслуживание репозитория в фоне
git maintenance stop     # Останавливает автоматическое обслуживание
git maintenance run      # Запускает задачи обслуживания вручную сразу
```

## 12. Worktree

**Git Worktree** позволяет иметь **несколько рабочих директорий** для одного репозитория.  
Это удобно, если нужно параллельно работать над разными ветками без переключения в одной директории.

```bash
git worktree list                # Показывает все подключённые рабочие директории
git worktree add <path> <bath>   # git worktree add ../feature-b feature-b
                                 # path   — путь к новой директории
                                 # branch — существующая или новая ветка
git worktree remove <path>       # Удаление рабочего дерева
```
