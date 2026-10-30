\# Лабораторная работа №6

\## Система контроля версий



\*\*Выполнил:\*\* студент группы 4516 Ростовцев А.С.



\*\*Репозиторий:\*\* https://github.com/rostovcevartem209/LR6



\## Цель работы



Изучить базовые возможности Git и получить опыт работы с локальным и удалённым репозиториями.



\## Ход выполнения работы



\### 1. Создание личной копии репозитория



На GitHub создана копия репозитория Kurtyanik/LR6 с помощью Fork.

Скопированы обе ветки: master и branch1.



!\[Личная копия репозитория](screenshots/01-fork.jpg)



\### 2. Проверка Git и настройка автора



Проверена установленная версия Git: 2.52.0.windows.1.

Настроены имя автора в формате «Группа Фамилия И.О.» и электронная почта.



!\[Версия Git и настройки автора](screenshots/02-git-config.jpg)



\### 3. Клонирование репозитория



Личный репозиторий склонирован на компьютер.

Проверены состояние рабочей папки и доступные ветки.



!\[Клонирование и проверка репозитория](screenshots/03-clone.jpg)



\### 4. Получение изменений с GitHub



Через веб-интерфейс GitHub создан файл github-file.txt.

Изменение зафиксировано в ветке master.



!\[Файл, созданный на GitHub](screenshots/04-github-file.jpg)



Командой git pull origin master изменения получены в локальный репозиторий.

Проверены содержимое файла и состояние рабочей папки.



!\[Получение изменений](screenshots/05-pull.jpg)



\### 5. Просмотр истории веток



Создана локальная ветка branch1 на основе origin/branch1.

Просмотрены история каждой ветки и общий граф коммитов.



При первом просмотре истории master была допущена опечатка в параметре команды.

После исправления команда выполнена успешно.



!\[История branch1 и общий граф](screenshots/06-history.jpg)



!\[История master](screenshots/06-history-master.jpg)



\### 6. Просмотр последних изменений



С помощью git show просмотрены последние коммиты веток master и branch1.

Командой git diff выполнено сравнение файла mergefile.txt между ветками.



!\[Последние коммиты обеих веток](screenshots/07-show-master-branch1.jpg)



!\[Различия файла между ветками](screenshots/08-diff.jpg)



\### 7. Слияние веток и разрешение конфликта



В ветке master выполнена команда git merge branch1.

Возник конфликт содержимого файла mergefile.txt, поскольку обе ветки изменили один участок файла.



!\[Конфликт при слиянии](screenshots/09-merge-conflict.jpg)



Файл открыт в Блокноте. Конфликт разрешён вручную:

удалены маркеры конфликта и сохранён согласованный вариант содержимого.

Исправленный файл добавлен в индекс, затем создан коммит слияния 715a0ed.



!\[Результат разрешения конфликта](screenshots/10-merge-resolved.jpg)



\### 8. Удаление побочной ветки



После успешного слияния локальная ветка branch1 удалена командой git branch -d branch1.

Её коммиты сохранились в истории master.



!\[Удаление локальной ветки](screenshots/11-delete-branch.jpg)



\### 9. Последовательная фиксация изменений



Создан файл progress.txt. Выполнены три отдельных коммита с комментариями:



\- 04112ae — создан файл с ходом выполнения лабораторной;

\- 060c295 — добавлена информация о слиянии веток;

\- 884dfc6 — добавлена временная строка для последующего отката.



!\[Три последовательных коммита](screenshots/12-commits.jpg)



\### 10. Откат коммита



Командой git revert --no-edit HEAD отменено последнее изменение.

Создан коммит cd8590c, удаляющий временную строку из progress.txt.

Предыдущие две строки файла сохранены. История коммитов не переписана.



!\[Откат последнего изменения](screenshots/13-revert.jpg)



\### 11. Создание ветки и оформление отчёта



Создана отдельная ветка report.

Отчёт оформляется в README.md с использованием Markdown.

Скриншоты размещены в папке screenshots.

Изменения отчёта фиксируются отдельными коммитами с комментариями.



!\[Создание ветки report](screenshots/14-report-branch.jpg)



\## Журнал команд



Ниже приведены команды выполненных этапов без результатов их выполнения.

В настройке почты использован адрес, указанный в аккаунте GitHub.



```bash

git --version

git config --global user.name "4516 Ростовцев А.С"

git config --global user.email "rostovcevartem209@gmail.com"

git config --global user.name

git config --global user.email



mkdir -p \~/Documents/GitLabs

cd \~/Documents/GitLabs

git clone https://github.com/rostovcevartem209/LR6.git

cd LR6

git status

git branch -a



git pull origin master

cat github-file.txt

git status



git branch branch1 origin/branch1

git --no pager log master --oneline --decorate

git --no-pager log branch1 --oneline --decorate

git --no-pager log --all --graph --oneline --decorate

git --no-pager log master --oneline --decorate



git --no-pager show master

git --no-pager show branch1

git --no-pager diff master branch1 -- mergefile.txt



git switch master

git merge branch1

git status

cat mergefile.txt

notepad mergefile.txt

git add mergefile.txt

git commit -m "Объединены master и branch1, разрешён конфликт mergefile.txt"

git status

cat mergefile.txt



git branch -d branch1

git branch

git --no-pager log --graph --oneline --decorate -8



echo "Лабораторная работа №6. Работа с Git." > progress.txt

git add progress.txt

git commit -m "Создан файл с ходом выполнения лабораторной"



echo "Выполнено слияние веток и разрешён конфликт." >> progress.txt

git add progress.txt

git commit -m "Добавлена информация о слиянии веток"



echo "Временная строка для демонстрации отката." >> progress.txt

git add progress.txt

git commit -m "Добавлена временная строка для последующего отката"



cat progress.txt

git --no-pager log --oneline -3

git status



git revert --no-edit HEAD

cat progress.txt

git --no-pager log --oneline -4

git status



git switch -c report

mkdir -p screenshots

git branch

explorer .

ls screenshots



notepad README.md

git add README.md screenshots

git commit -m "Начат отчёт: добавлены первые этапы работы и скриншоты"

git status

```

