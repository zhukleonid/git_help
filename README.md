# Краткая инструкция по работе с системой Git и платформой GitHub

## __Введение в Git и GitHub__ 

<br>

[**Git**](https://git-scm.com/) — это система контроля версий, которая помогает отслеживать изменения в проекте. Этот инструмент можно использовать как для индивидуальной, так и для командной работы.

Git позволяет сохранять изменения локально и при необходимости возвращаться к предыдущим версиям проекта. Также можно создать удалённую копию на хостинг-платформе, которая работает с Git, и поделиться результатом с другими.

[**GitHub**](https://github.com/) — платформа для хранения IT-проектов и совместной работы над ними с использованием Git. По сути, это сайт, куда можно загрузить файлы своего проекта для обмена с другими людьми.

С английского языка слово **hub** переводится как *«узловая станция»*. И действительно, **GitHub** стал самым популярным сайтом для хранения **Git-репозиториев**. Многие крупные компании, такие как *Google, Apple, Valve* используют **GitHub** для своих проектов. 

**Git и GitHub** — это два разных проекта, которые развиваются независимо друг от друга. 

<br>

    Git:
    - консольный инструмент для работы с локальными и удалёнными репозиториями;
    - проект с открытым исходным кодом.

    GitHub:
    - платформа для размещения удалённых репозиториев;
    - принадлежит компании Microsoft.

<br>

## __Инициализация репозитория__

<br> 

### *Сделать папку репозиторием*

<br> 

Чтобы Git начал отслеживать изменения в вашем созданном проекте, папку с файлами этого проекта нужно сделать Git-репозиторием. Для этого следует переместиться в неё и ввести в терминале команду: 

<br>

```
git init
```

<br>

После успешного выполнения данной команды в папке проекта появится скрытая папка `.git`. Проверить наличие скрытой папки можно с помощью команды:

<br>

```
ls -a
```

<br>

### *Проверить состояние репозитория* 

<br>

После инициализации репозитория запустить команду:

<br>

```
git status 
```

<br>

Команда показывает текущее состояние вашего репозитория.

<br>

## __Добавление файлов в репозиторий__

<br>

### *Подготовка файлов к сохранению*

<br>

Для сохранения файлов в репозитории необходимо сделать их отслеживаемыми системой. Для этой задачи выступает команда:

<br>

```
git add
```

<br>


Следует помнить, что команда `git add` не сохраняет содержимое файлов в репозитории. 

Само сохранение, или фиксацию состояния файлов, называют **коммитом** (от англ. commit — *«совершать», «фиксировать»*). «Сделать коммит» значит сохранить текущую версию файла. 

<br>

## __Коммиты__

<br>

**Коммит** — это одна из основных сущностей в Git (и в других системах контроля версий). Коммит гарантирует, что изменения будут сохранены в истории и при необходимости к ним можно будет «откатиться». 

<br>

### *Выполнение коммита*

<br>

Сделать коммит можно командой:

<br>

```
git commit c ключом -m 
```

<br>

**m** - (от англ. message — *«сообщение»*), флаг присваивает коммиту сообщение.

Обычно в таком сообщении поясняется, в чём именно состояли изменения. Это как заметки на полях: благодаря им проще читать и понимать текст. Сообщение коммита выполняет те же функции — улучшает понимание и упрощает навигацию. Оно пишется после ключа `-m` в кавычках.

<br>

## __История коммитов__

<br>

Для отображения истории коммитов используется команда: 

<br>

 ```
 git log
 ```

 <br>

 ### *Идентификатор коммита в истории*

<br>

При исполнении команды `git log` в выводе терминала вы увидите историю коммитов. В первой строке истории каждого коммита после слова `commit` содержится **хеш**. 

**Хеш** - это основой уникальный идентификатор коммита. Обычно хеш — это короткая (40 символов в случае SHA-1) строка, которая состоит из цифр 0—9 и латинских букв A—F (неважно, заглавных или строчных). 

Git хранит таблицу соответствий `хеш → информация о коммите`. Если вы знаете хеш, вы можете узнать всё остальное: автора и дату коммита и содержимое закоммиченных файлов. 

## __Создание удаленного репозитория на GitHub__

<br>

### *Инструкция по созданию репозитория на GitHub*

<br>

Удаленный репозиторий требуется для хранения вашего локального репозитория. Для того, чтобы создать удаленный репозиторий на платформе GitHub должен выполняться следующий порядок действий:

1. Зайдите в свой профиль по ссылке `https://github.com/username`, где **username** — имя, которое вы указали при регистрации;
2. Создайте репозиторий. Для этого перейдите на вкладку **Repositories** (англ. *«репозитории»*), а затем нажмите на зелёную кнопку **New** (англ. *«новый»*) справа; 
3. Открылось окно создания нового репозитория. Назовите его, например **MyRepo**. Название удалённого репозитория необязательно должно совпадать с именем папки проекта у вас на компьютере. Но чтобы не путаться, советую называть их одинаково. 
 Далее нажимите на зелёную кнопку **Create repository** (англ. *«создать репозиторий»*) внизу.

<br>

## __Синхронизация локального и удаленного репозиториев__

<br>

### *Генерация SSH-ключа*

<br>

Для того, чтобы вы могли передавать данные из локального в удаленный репозиторий или скачивать файлы из удаленного в локальный репозиторий, необходимо их безопасно синхронизовать. Синхранизация происходит с использованием SSH-ключа. 

Инструкция по генерации **SSH-ключа**:

1. Для генерации **SSH-пары** можно использовать программу **ssh-keygen**. Откройте терминал и введите следующую команду:

    ```
    $ ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
    ```

2. Укажите место хранения ключей. Простой вариант — сделать домашний каталог пользователя путём по умолчанию. Для этого нажмите Enter.

    **macOS**

    ```

    > Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter] 

    ```
    **Windows**

    ```

    > Enter a file in which to save the key (C:\Users\<имя_пользователя>\.ssh\):[Press enter] 

    ```

    Теперь в указанной директории появится пара ключей.

3. Программа запросит кодовую фразу (англ. **passphrase**) для доступа к **SSH-ключу**. Вы можете оставить поле пустым. Для этого нажмите **Enter**, а затем ещё раз **Enter** для подтверждения.

    ```

    > Enter passphrase (empty for no passphrase): [Type a passphrase]
    > Enter same passphrase again: [Type passphrase again] 

    ```
4. Готово! Теперь осталось проверить, что ключи действительно сгенерировались. Для этого вызовите команду:

    ```

    ls -a ~/.ssh 

    ```

  На экране должны появиться два файла — один с расширением **.pub**, другой — без. Файл в **.pub** — публичный, им можно делиться с веб-сайтами или коллегами. Файл без расширения **.pub** — приватный. Ни в коем случае не передавайте его никому! 
  
  <br>

### *Привязка SSH-ключа к GitHub*

<br>

Для синхронизации и безопасной передачи данных необходимо связать **SSH-ключ** на **GitHub**.

<br>

Инструкция по связыванию **SSH-ключа** и GitHub-аккаунта:
    
1. Введите команду в терминал `cat ~/.ssh/id_rsa.pub` или `cat ~/.ssh/id_ed25519.pub`  в зависимости от ранее выбранного алгоритма шифрования и скопируйте вывод в буфер обмена из консоли;
2. Перейдите на **GitHub** и выберите пункт **Settings** (англ. *«настройки»*) в меню аккаунта;
3. В меню слева нажмите на пункт **SSH** and **GPG keys**;
4. В открывшейся вкладке выберите **New SSH key** (англ. *«новый SSH-ключ»*);
5. В поле **Title** (англ. *«заголовок»*) напишите название ключа. Например, **Personal key** (англ. *«личный ключ»*);
6. В поле **Key type** (англ. *«тип ключа»*) должно быть **Authentication Key** (англ. *«ключ аутентификации»*);
7. В поле **Key** скопируйте ваш ключ из буфера обмена;
8. Нажмите на кнопку **Add SSH key** (англ. *«добавить SSH-ключ»*);
9. Проверьте правильность ключа с помощью следующей команды `$ ssh -T git@github.com`. 


<br>

### *Связывание локального и удалённого репозитория*

<br>

Привязка удаленного репозитория к локальному производится командой: 

<br>

```
git remote add 
```

<br>

Для того чтобы произвести данную операцию необходимо перейти на страницу удаленного репозитория, выбрать тип **SSH** и скопировать **URL**. 

Открыть консоль, перейти в каталог локального репозитория и ввести команду `git remote add`.

<br>

```
$ cd ~/dev/first-project
$ git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git 
```

<br>

Команде необходимо передать два параметра: **имя** удалённого репозитория и его **URL**. В качестве имени используйте слово **origin**. А **URL** вы скопировали со страницы удалённого репозитория.

Убедиться, что репозитории связаны, команда ` - git remote -v`

<br>

```
$ git remote -v
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push) 
```
<br>

В выводе вы должны увидеть две строчки, аналогичные тем, что показаны выше.

<br>

### *Синхронизация локального и удалённого репозитория*

<br>

Отправить изменения на удалённый репозиторий: 

<br>

```
git push
```
<br>

В первый раз эту команду нужно вызвать с флагом -u и параметрами origin (имя удалённого репозитория) и main или master (название текущей ветки). Флаг -u свяжет локальную ветку с одноимённой удалённой. 


