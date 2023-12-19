# Работа с GitHub

## Начальные команды Git
- pwd проверить в какой директории находимся
- cd ~ сменить директорию
- ls содержимое диретории
- ls -a скрытые файлы
- touch создание файла
- mkdir создание папки
- cp копирование файлов
- mv пермещение файлов
- mkdir -p создание структуры папок
- cat чтение файлов
- rm удаление файла
- rmdir удаление папок
- rm -r удаление папок со всем содержимым
- && позволяет выполнять сразу несколько операций
- ↑ обратиться к предыдущей команде
- Tab два раза автозаполнение
- Tab cd + Tab автоопределение пути директории
- ~ - перемещение в корневую и домашнюю директории
- git version версия Git
- $ git config --global user.name "User Namovich" 
# имя или ник нужно написать латиницей и в кавычках
- $ git config --global user.email username@yandex.ru
# здесь нужно указать свой настоящий email 
- $ cat ~/.gitconfig проверка
- $ git config --list конфигурации git
- git init # создали репозиторий 
- rm -rf .git # удалили подпапку .git   
- git status статус Git
- git add --all # подготовили к сохранению все файлы в репозитории
- git commit -m 'Мой первый коммит!' сохранить изменения
- git log история коммита

## GitHub
### Создание рипозитория
- ls -la .ssh/ # вывели список созданных ключей 
- ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" генерация ключа
- ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
- ls -a ~/.ssh Эта команда покажет содержимое папки .ssh.
- ls -la ~/.ssh Эта команда покажет содержимое папки .ssh в виде списка файлов.

### Привязываем SSH-ключ к GitHub

`# скопировать содержимое ключа в буфер обмена:
$ clip < ~/.ssh/id_rsa.pub
# для ed25519:
$ clip < ~/.ssh/id_ed25519.pub

- Перейдите на GitHub и выберите пункт Settings (англ. «настройки») в меню аккаунта. В меню слева нажмите на пункт SSH and GPG keys.`
- В открывшейся вкладке выберите New SSH key (англ. «новый SSH-ключ»).
- В поле Title (англ. «заголовок») напишите название ключа. Например, Personal key (англ. «личный ключ»).
- В поле Key type (англ. «тип ключа») должно быть Authentication Key (англ. «ключ аутентификации»).
- В поле Key скопируйте ваш ключ из буфера обмена.
. Нажмите на кнопку Add SSH key (англ. «добавить SSH-ключ»).
- Проверьте правильность ключа с помощью следующей команды.
  ssh -T git@github.com 
- [Проверка ключа](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints)

### Привязка удаленного репозитория к локальному

- git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git 
- git remote -v убедиться, что репозитории связаны
- git push -u origin main отправить изменения на удаленный репозиторий первый раз
- git push потом
- [Шпаргалки по MD](https://gist.github.com/fomvasss/8dd8cd7f88c67a4e3727f9d39224a84c)
- [Шпаргалки по MD](https://gist.github.com/fomvasss/8dd8cd7f88c67a4e3727f9d39224a84c)
- that's all

### Новые команды 

- git log --oneline - Получить сокращённый лог.

HEAD - это голова. Head -> master - он указывает на последний коммит.

$ pwd %% посмотрели, где мы
```mermaid
$ cd .git %% комментарий
$ ls %% посмотрели, какие есть файлы.
COMMIT_EDITMSG  ORIG_HEAD  description  index  logs/     refs/
HEAD config     hooks/       info/  objects/
$ cat HEAD %%  команда cat показывает содержимое файла.
ref: refs/heads/master %% в файле вот такая ссылка
$ cat refs/heads/master # взяли ссылку из файла HEAD
# внутри хеш
e007f5035f113f9abca78fe2149c593959da5eb7

$ git log 
%% сверяем с хешем последнего коммита
commit e007f5035f113f9abca78fe2149c593959da5eb7
Author: John Doe <johndoe@example.com>
Date:   Tue Mar 28 00:26:53 2023 +0300

    hash

... %% другие коммиты
%% статусы 
untracked %% не отслеживаемый
staged %% подготовленный
tracked %% отслеживаемый
modified --> изменённый
```

graph LR;
  untracked -- "git add" --> staged(+tracked);
  staged    -- "git commit"     --> tracked/comitted; %% tracked в списке на коммит.
  modified  -- "git add"     --> staged/modified/tracked;
%% стрелка без текста для примера: 
  A --> B;
%% - это в mermaid комментарии.
Коммит -- это всему голова.
Статусы файлов:
<тут пустая строка!>

```mermaid
%% описание схемы
```
<и тут пустая строка!>

# How to develope

```mermaid
flowchart TD
A [Develope to production] --> B{is it friday?};
```
Here is a simple flow chart:

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```