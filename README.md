# G i t
 
## 1. Генерация SSH ключа
Созадние каталога, назначение владельца и установка разрешений:
```bash
mkdir ~/.ssh
chown -R user:user ~/.ssh/
chmod 700 ~/.ssh/
```
Переход в каталог и генерация ssh ключа:
```bash
cd ~/.ssh && ssh-keygen
 или
cd ~/.ssh && ssh-keygen -t ed25519 -C "email@exammple.com"
```
Публичную часть необходимо залить на GitHub / GitLab.

## 2. Автодополнение названия git ветки и текщего времени в терминале
Для изменения стандартной строки приглашения терминала, нужно изменить файл настроек терминала ~/.bashrc и добавить скрипт git.  
Добавим в конец файла ~/.bashrc специальные строки:
```bash
. ~/git-prompt.sh
export GIT_PS1_SHOWDIRTYSTATE=1
export PS1='\[\033[36m\] \w:$(__git_ps1 "\[\033[32m\](%s)")\[\033[34m\]$ \[\033[37m\]' 
```
или с выводом текущего времени:
```bash
. ~/git-prompt.sh
export GIT_PS1_SHOWDIRTYSTATE=1
export PS1='\[\033[36m\] \u@\h \w$(__git_ps1 "\[\033[32m\](%s)")\[\033[34m\]$ \[\033[37m\]'
```

Перейти в домашний каталог и скачать скрипт git-promt.sh:
```bash
cd ~
wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh
```

Перезагружаем настройки .bashrc без выхода и повторного входа:
```bash
source ~/.bashrc
```

## 3. Команды статусов и получения дополнительной информации 
Просмотр версии приложения git:
```bash
git verion
```
Инициализация нового репозитария:
```bash
git init
```
Текущее состояние:
```bash
git status
```
Получение подробной информации о последнем коммите:
```bash
git show
```
Получение подробной информации о указанном коммите:
```bash
git snow 772685b780259c4313d1f489a47f4c1dccc19266
```
Просмотр всех имеющиеся коммитов с их ID и комментариями:
```bash
git log
```
Cписок всех выполненных операций и изменений:
```bash
git reflog
```

## 4. Отслеживание изменений
Добавление определенного файла в отслеживание:
```bash
git add README.md
```
Добавление всех файлов в отслеживание из текущей директории:
```bash
git add .
```
Исключение указанного файла из отслеживания:
```bash
git rm --cached ./Lesson_01/.terraform
```
Рекурсирвное исключение файлов из отслеживания:
```bash
git rm -r --cached ./Lesson_03/.terraform/
```

## 5. Работа с коммитами
Коммит файлов репозитария:
```bash
git commit -m "My First Commit"
```
Одновременное добавление и коммит всех ранее добавленных файлов:
```bash
git commit -am "My Add and commit"
```
Правка комментария к последнему коммиту:
```bash
git commit --amend
```
Добавление файла в последней коммит:
```bash
git add missed-file.txt
git commit --amend
```

## 6. Задание исключений 
Создание файла в котором будут задаваться исключаемые файлы:
```bash
touch .gitignore
```
Примеры исключений файлов из отслеживания, находящиеся в .gitignore:
```bash
*.py[cod]             # будут игнорироваться файлы следующих расширений: *.pyc, *.pyo, *.pyd
name.yaml             # игнорируется один конкретный файл
log/                  # игнорируется папка log
resources/main.json   # игнорируется файл находящийся в папке
```

## 7. Идентификация пользователя для коммитов
Задание констант имени и емейла для всей системы, которые отражаютмся в коммитах:
```bash
git config --system user.name "MyUserNamE"
git config --system user.email "MyEmail"
```
Задание констант имени и емейла для всех репозиториев одного конкретного пользователя:
```bash
git config --global user.name "MyUserName"
git config --global user.email "MyEmail"
```
Задание констант имени и емейла для одного конкретного репозитария:
```bash
git config --local user.name "MyUserName"
git config --local user.email "MyEmail"
```

## 8. Работа с ветками репозитария
Просмтор всех имеющихся веток проекта:
```bash
git branch -a
```
Создание новой ветки new-api2:
```bash
git branch new-api2
```
Переход в ранее созданную ветку new-api:
```bash
git checkout new-api
```
Создает и переходит в новую ветку new-api2:
```bash
git checkout -b new-api2
```
Cлияние веток
```bash
git merge new-api
```
Удаление ветки которая была хотя бы единожды cмержена:
```bash
git branch -d new-api
```
Удаление ветки, которая не была ни разу смержена:
```bash
git branch -D new-api
```
Синхронизация локальных веток с ветками удаленного репозитария:
```
git fetch --prune
```
или
```
git fetch -p
```


## 9. Работа с внешним Git репозитарием
Просмотр имёни/адреса внешнего репозитария, связанного с текущим локальным репозитарием:
```bash
git remote -v
```
Более детальный вывод информация о именах и адресах удаленных репозитариев:
```bash
git remote show origin
```
Добавление внешнего адреса репозитария с именем origin:
```bash
git remote add origin git@github.com:skytorin/Terraform.git
```
Переименование имени внешнего адреса из origin в origin2:
```bash
git remote rename origin origin2
```
Удаление адреса внешнего репозитария с именем origin:
```bash
git remote rm origin
```
Показывает изменения в файле с момента последнего коммита:
```basg
git diff
```

## 10. Получение и отправка изменений в удаленный реозитарий
Получить последние изменения с удалённого репозитария:
```bash
git pull <remote-name> <branch-name>
```
или
```bash
git pull
```
Отправка изменений в удаленный репозиторий:
```bash
git push <remote-name> <branch-name>
```
или
```bash
git push -u origin master
```
или
```bash
git push
```

## 11. Отмена и откат изменений  
Отмена последнего коммита в локальном репозитарии:
```bash
git reset HEAD~
```
Полное удаление последего коммита, включая все изменения файлов данного коммита:
```bash
git reset --hard HEAD~1
```
Откат к произвольному коммиту по его индексу:
```bash
git reset HEAD@{index}
```

## 12. Восстановление удаленных файлов (после git rm)
Обычно чтобы просто откатить состояние файла до исходного в текущей версии (даже после ручного удаления), нужно сделать такой чекаут
```bash
git checkout -- file_name.ext
```
Если удаление делалось через git rm, то счекаутить обратно состояние не получится. 
Поэтому надо сделать сначала ресет файла в индексе, а уже потом чекаут
```bash
git reset -- file_name.ext
git checkout -- file_name.ext
```
Если после add, но до коммита найден ошибочно добавленный файл/папка, то такой же ресет поможет убрать его из следующего коммита

## Решение проблем
Длинна пути в Windows не может превышать 260 символов, это можно обойти.
Меняем в реестре значение параметра LongPathsEnabled с 0 на 1:
```bash
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem\LongPathsEnabled
```
Меняем настройки самого Git  
```bash
git config --system core.longpaths true
```


## Git Flow Merge Request
Выводим имеющиеся ветки репозитария:
```bash
git branch -a
```

Переходим в локальную ветку master и обновляем ее:
```bash
git checkout master
git pull
```

Создаем новую ветку от master, переходим в нее и отправляем новую ветку в удаленный репозитарий:
```bash
git branch release-1.0.0
git checkout release-1.0.0
git push --set-upsteram origin release-1.0.0 
```
Вносим изменения в новой ветке (Created/Added/Edited feature)  
Добавляем все файлы в отслеживание и комитим, после чего отправляем изменения в удаленный репозитарий: 
```bash
git commit -am "Created Feature"  
git push
```

В UI Gitlab создаем новый merge request (release-1.0.0 to master). Добавлем описание и ревьювера.
Ждем согласования и подтверждения:
```bash
Create Merge Request / /Pull Request  ---> Approve ---> Merge
```

После подверждения merge request обновляем локальную ветку master.  
Переходим в ветку master и обновляем:  
```bash
git checkout master
git pull
```

Удаляем смерженную ветку release-1.0.0:  
```bash
git fetch -p
```



