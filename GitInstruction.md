![Logo](Git-Logo-1788C.png)
# Работа с Git и GitHub

## 1. Проверка наличия установленного Git
В терминале выполнить команду `git version`.
Если Git установлен, появится сообщение с информацией о версии программы. Иначе будет сообщение об ошибке.

## 2. Установка Git
Загружаем последнюю версию с сайта https://git-scm.com/downloads.
Устанавливаем с настройками по умолчанию.

## 3. Настройка Git
При первом использовании Git необходимо представиться. Для этого нужно ввести в терминале две команды:
```
git config --global user.name "Ваше имя английскими буквами"
git config --global user.email ваша почта почта@example.com
```

## 4. Инициализация репозитория
Получить репозиторий можно двумя способами.
1. В терминале перейти к папке, в которой хотим создать репозиторий. И выполняем команду:
```
git init
```
В исходной папке появится скрытая папка *.git*

2. Клонировать существующий репозиторий Git из любого места. Сделать это можно с помощью команды:
```
git clone <адрес репозитория>
```

## 5. Запись изменений в репозиторий
**1. Проверка состояния файлов.** Основным инструментом для получения информации от git о его текущем состоянии является команда:
```
git status
```
**2. Отслеживание новых файлов.** Чтобы добавить файл или файлы к следующему коммиту, воспользуйтесь командой:
```
git add <имя файла,который надо добавить>
```
 Писать название файла целиком не надо, только первые две буквы,затем если нажать Tab, терминал самостоятельно заполнит то, что надо написать.

**3. Просмотр изменений.** Чтобы увидеть разницу между текущим файлом и закоммиченным файлом,воспользуйтесь командой:
```
git diff
```
Важно отметить, что *git diff* сама по себе не показывает все изменения сделанные с последнего коммита – только те, что ещё не проиндексированы. 

**4. Зафиксировать или сохранить.** Сообщение фиксации можно задать в команде *commit*, поставив перед ним флаг *-m*:
```
git commit -m "Текст сообщения"
```
Версия предоставит ряд данных о себе: 
* зафиксированная ветка (master);
* контрольная сумма SHA-1 версии;
* количество подвергшихся изменениям файлов; 
* статистику добавленных и удаленных строк. 

В Git есть простой способ обойтись без области индексирования. Достаточно передать команде *git commit* параметр *-a*, и система Git начнет автоматически индексировать все отслеживаемые файлы перед их фиксацией, позволяя обойтись без команды *git add*.
```
git commit -a -m "Текст сообщения"
```

## 6. Журнал изменений.
 После сохранения нескольких версий файлов или клонирования уже существующего репозитория, можно вывести на экран истории всех коммитов с их хеш-кодами. Для этого воспользуйтесь командой:
```
git log
```
В таблице представлены самые распространенные параметры команды *git log*.
|Параметр|Описание|
|--------------|-----------------|
|-p|Показывает изменения, внесенные в каждую версию|
|--start|Показывает статистику измененных файлов в каждом коммите|
|--shortstat|Показывает только строку с изменениями/вставками/удалениями от команды `--stat`
|--name only|Показывает список измененных файлов после информации о коммите|
|--name status|Показывает список измененных файлов с информацией о добавлении/изменении/удалении|
|--abbrev-commit|Показывает только первые несколько символов контрольной суммы SHA-1 вместо всех 40|
|--relative date|Показывает дату не в полном, а вотносительном формате (например, "2 недели назад")|
|--graph|Показывает ASCII-граф истории ветвлений и слияний вместе с выводом команды `log`
|--pretty|Показывает коммиты в альтернативном формате.Возможны параметры `oneline`,`full`,`fuller` и `format` (с указанием ваше версии формата)|

## 7. Переключение между сохранениями(коммитами)
 1. Для того, чтобы перейти от одного коммита к другому, воспользуйтесь командой:
```
git checkout <первые четыре символа (коммит), на который необходимо переключиться>
```
2. Для того,чтобы вернуться к актуальному состоянию и продолжить работу,необходимо выполнить команду:
 ```
 git checkout master
 ```

## 8. Игнорирование файлов
Для того, чтобы исключить из отслеживания определенные файлы или папки необходимо создать там файл ***.gitignore*** и записать в него их названия или шаблоны, соответствующие таким файлам или папкам.

К шаблонам в файле .gitignore применяются следующие правила:
* Пустые строки, а также строки, начинающиеся с **`#`**, игнорируются.
* Стандартные шаблоны являются глобальными и применяются рекурсивно для всего дерева каталогов.
* Чтобы избежать рекурсии используйте символ слеш **`(/)`** в начале шаблона.
* Чтобы исключить каталог добавьте слеш **`(/)`** в конец шаблона.
* Можно инвертировать шаблон, использовав восклицательный знак **`(!)`** в качестве первого символа.

## 9. Создание веток в Git
По умолчанию имя основной ветки в Git - *master*.
Создать ветку можно командой:
```
git branch <имя новой ветки>
```
Список веток в репозитории можно посмотреть с помощью команды `git branch`.
Текущая ветка будет отмечена звездочкой: **\*master**

Создать ветку и сразу перейти туда позволяет команда `git checkout` с параметром `-b`:
```
git checkout -b <имя новой ветки>
```
Важно помнить, что при смене веток Git возвращает рабочую папку в то состояние, которое она имела на момент последнего коммита этой ветки.
 
## 10. Слияние веток и разрешение конфликтов
Для слияния выбранной ветки с текущей нужно выполнить команду:
```
git marge <название выбранной ветки>
```
Если была изменена одна и та же часть файла в обеих ветках, то может возникнуть конфликт, который потребует участия пользователя.
VSCode предлагает варианты разрешения.

Система Git добавляет к проблемным файлам стандартные метки, для разрешения конфликта следует выбрать одну из версий. Разобравшись с каждым проблемным файлом,необходимо выпонить для каждого из этих файлов команду *git add*. Индексируя файл, помечаем его как неконфликтующий.

 Для разрешения конфликтов можно вызвать графический интерфейс командой:
```
git mergetool
```

Удостоверившись в том, что все ранее конфликтовавшие файлы проиндексированы, остается завершить слияние командой *git commit <Текст сообщения>*.

## 11. Удаление веток
Ветки в общем случае удаляются 
командой:
```
git branch -d
```
Если удаляемая ветка содержит данные, не подвергшиеся слиянию, удалить ее командой **`git branch –d не получится`**. Тогда используйте параметр **`-D`**.

## 12. Работа с удаленными репозиториями 

1. Создать аккаунт на GitHub.com
2. Создать локальный репозиторий
3. Создать удаленный репозиторий
4. Связать удаленный репозиторий с локальным

Добавить удаленный репозиторий к проекту можно с помощью команды:
```
git remote add <имя для репозитория> <url - адрес репозитория в сети>
```
Для получения и слияния изменений из удаленного репозитория используется команда: 
```
git pull
```
Для того, чтобы поделиться своими наработками, необходимо отправить их в удалённый репозиторий с помощью команды: 
```
git push <имя удаленного репозитория> <имя ветки, которую нужно отправить>.
```
В командной работе удобно объединять изменения не на локальном репозитории каждого участника, а на удаленном. Для этого существует команда `pull request`, то есть запрос на изменения.

**Как сделать pull request:** 

* Делаем   (ответвление) репозитория fork
* Делаем **`git clone`** **своей** версии репозитория
* Создаем новую ветку и в **нее** вносим свои изменения
* Фиксируем изменения (делаем коммиты)
* Отправляем свою версию в свой GitHub
* На сайте GitHub нажимаем кнопку **`pull request`**