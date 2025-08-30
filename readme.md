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
git merge <branch_name>         # Слить ветку с текущей
git branch -d <branch_name>     # Удалить ветку
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
git checkout -- <file>           # Отменить изменения в файле
git reset HEAD <file>            # Убрать файл из индекса
git reset --soft <commit_hash>   # Откат к коммиту (сохраняя изменения)
git reset --hard <commit_hash>   # Откат к коммиту без сохранения
git revert <commit_hash>         # Отменяющий коммит другого коммита
```

## 9. Информация Git

```bash
git --version   # Версия Git
```
