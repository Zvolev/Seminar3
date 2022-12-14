# **Инструкция по пользованию сиситемой контроля версий Git**

![Эмблема](git.png)

*Git* - это набор консольных утилит, которые отслеживают и фиксируют изменения в файлах (чаще всего речь идет об исходном коде программ, но вы можете использовать его для любых файлов)

# Определение глобальных настроек, создание репозитория и добавление файла

После установки ПО и первом входе в терминал потребуется установка глобальных настроек. но самыми главными, без которых Git откажется продолжать работать, будут реквизиты пользователя. Вводим мы их с помощю команд

    git config --global.name "Evgen"
    git config --global.email "zvolev@mail.ru"

Чтобы определить Git с какой папкой мы будем работать, мы используем команду инициализации репозитория

    gif init

Среда для отслеживания версий ГОТОВА!!!

Далее через миню VSCode в нашей папке создаем файл, с которым и будем дальше работать. Но пока Git его видит, но не отслеживает... Увидеть состояние файла в репозитории можно через команду

    git status

Чтобы добавить файл, изменения которого должен отслеживать Git, мы воспользуемс командой

    git add <Имя файла>
    
Этой же командой в дальнейшем мы будем добавлять изменения в конкретном файле, либо все изменения в репозитории

    git add . 

или
 
    git add -A

## Создание и изменение версий (коммитов)

Когда появляется необходимость создать версию файла, нужно сохранить изменения в файл, с помощью ранее описанной команды "add" добавить изменения в репозиторий и создать версию файла с помощью команды

    git commit -m "сообщение-коментарий"

Если есть необходимость перезаписать, ранее созданную версию, можно воспользоваться командой

    git commit --amend -m 'новое сообщение-комментарий'

## Просмотр списка версий и сравнение изменений

Для просмотра списка записанных версий воспользуемся командой

    git log
    git log --oneline

Использование данной команды с флагом --oneline выводит список версий в однострочном сокращенном виде.

для просмотра изменений с последней сохраненной версии до текущей версии используется команда 

    git diff

А если к этой команде добавим названия сохраненных коммитов, то увидим изменения между этими версиями, при чем полное название коммитов можно не писать - достаточно шести первых символов названия

    git diff 65ee7t 645r7ee

В зависимости от таго в каком хронологическом порядке будут указанны коммиты, будут отображены изменения (инверсия отображения информации)

## Просмотр определенной версии

Для просмотра определенной версии файла воспользуемся командой 

    git checkout <название коммита>

Чтобы вернуться к последней версии введем в терминале 

    git checkout master

Ворачиваться к последней версии перед сохранением очередного коммита обязательно!

Команду add и commit можно объеденить, но делать это надо с осторожностью, со знанием дела. Выглядеть такая формула будет вот так

    git commit -am "сообщение-коментарий"


# _**Ветвление в Git**_

*Ветвление в Git* позволяет вести параллельную работу, работу над различными версиями или независимую работу, например при тестировании, когда мы не используем основной код, а работаем над его клоном...

## Создание новой ветки

Для создания новой ветки воспользуемся командой
    
    git branch <name_branch>

Что бы вносить изменения из этой ветки - нужно в нее перейти при помощи команды

    git checkout <name_branch>

После внесения изменений в версию делаем коммит и у нас сохраняется версия в отдельной ветке...

## Слияние и удаление

Отработав версию, в которой может быть больше одного коммита, мы можем произвести слияние с Master-веткой (версией) и для этого воспользуемс командой 

    git merge <name_branch>

При этом надо брать во внимание, тот факт, что слияние происходит из указанной ветки в ветку в которой мы находимся в данный момент.
При слиянии может произойти конфликт, который, при работе в GUI средах может разрешиться по встроенным алгоритмам, иначе нам придется воспользоваться редактором слияния (GUI) или вручную приводить к требуемому виду...

После слияния, если мы не собираемся более работать в ветке - мы можем ее удалить

    git branch -d <name_branch>


## Просмотр лога

Для просмотра лога (истории версий) воспользуемся командой 

    git log

Она информативная, но исбыточно. Чтобы вывести информацию в однострочном виде для каждого коммита воспользуемся параметром 
    git log --oneline

Но с такой командой и параметром информация выводится только для ветки , вкоторой мы находимся в данный момент.
Еще два добавленных параметра к этой команде помогут нам увидеть историю коммитов для всех веток и в слегка графическом виде

    git log --all --oneline --graph

![скрин1](Scr.png)

### Итоги раздела

В этом разделе мы узнали основные команды для работы в Git по схеме ветвления. Их будет достаточно, но это только основные команды - есть еще много команд специфических, практичных и удобных в определенной ситуации. с ними можно ознакомится в соответствующей литературе...

# Удаленная работа

## Удаленный репозиторий

### Самый удаленный репозиторий

