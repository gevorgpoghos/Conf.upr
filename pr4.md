## Задача 1
На сайте https://onlywei.github.io/explain-git-with-d3 или http://git-school.github.io/visualizing-git/ (цвета могут отличаться, есть команды undo/redo) с помощью команд эмулятора git получить следующее состояние проекта (сливаем master с first, перебазируем second на master): см. картинку ниже. Прислать свою картинку.

![image](https://github.com/user-attachments/assets/5a18a59f-8fa1-4924-a2b4-7bce7553379f)
```
git commit
git tag in
git branch first
git branch second
git commit
git commit
git checkout first
git commit
git commit
git checkout master
git merge first
git checkout second
git commit
git commit
git rebase master
git checkout master
git merge second
git checkout in
```

## Задача 2
![Screenshot 2024-11-08 092125](https://github.com/user-attachments/assets/bbdb6616-dc15-440c-9549-59f35faaa1a3)
![Screenshot 2024-11-08 092056](https://github.com/user-attachments/assets/e9659a00-f9ec-4260-8d67-9a68aef679ef)

```
Gev@DESKTOP-HIQHO4E MINGW64 ~/Desktop
$ mkdir my

Gev@DESKTOP-HIQHO4E MINGW64 ~/Desktop
$ cd my

Gev@DESKTOP-HIQHO4E MINGW64 ~/Desktop/my
$ git init
Initialized empty Git repository in C:/Users/Gev/Desktop/my/.git/

Gev@DESKTOP-HIQHO4E MINGW64 ~/Desktop/my (master)
$ git config user.name "gevorgpoghos"

Gev@DESKTOP-HIQHO4E MINGW64 ~/Desktop/my (master)
$ git config user.email "armgamonl@gmail.com"

Gev@DESKTOP-HIQHO4E MINGW64 ~/Desktop/my (master)
$ nano prog.py

Gev@DESKTOP-HIQHO4E MINGW64 ~/Desktop/my (master)
$ git add prog.py
warning: in the working copy of 'prog.py', LF will be replaced by CRLF the next time Git touches it

Gev@DESKTOP-HIQHO4E MINGW64 ~/Desktop/my (master)
$ git config --global core.autocrlf false

Gev@DESKTOP-HIQHO4E MINGW64 ~/Desktop/my (master)
$ git add prog.py

Gev@DESKTOP-HIQHO4E MINGW64 ~/Desktop/my (master)
$ git commit -m "Добавление файла"
[master (root-commit) 5ef0a2d] Добавление файла
 1 file changed, 1 insertion(+)
 create mode 100644 prog.py

```

## Задача 3
![Screenshot 2024-11-08 093305](https://github.com/user-attachments/assets/1deb9376-7697-4395-8c6a-a27a69122351)

```
git init
git config user.name "gevorgpoghos"
git config user.email "armgamonl@gmail.com"
echo 'print("Hello, World!")' > prog.py
git add prog.py
git commit -m "first commit"

# Создание bare-репозитория
mkdir -p repository
cd repository
git init --bare server

# Возвращение в основной репозиторий, подключение к серверу и пуш
cd ..
git remote add server repository/server
git remote -v
git push server master

# Клонирование серверного репозитория в клиентский
git clone repository/server repository/client
cd repository/client
git config user.name "gevorgpoghos2"
git config user.email "armgamonll@gmail.com"

# Добавление нового файла и коммит
echo "Author Information:" > readme.md
git add readme.md
git commit -m "docs"

# Переименование удаленного репозитория и пуш
git remote rename origin server
git push server master

# Возвращение в основной репозиторий, чтобы сделать pull
cd ..
git pull server master --no-rebase  # Используем merge вместо rebase

# Внесение изменений от gevorgpoghos и пуш
echo "Author: gevorgpoghos" >> readme.md
git add readme.md
git commit -m "gevorgpoghos info"
git push server master

# Переход в клиентский репозиторий и внесение изменений от gevorgpoghos2
cd client
echo "Author: gevorgpoghos2" >> readme.md
git add readme.md
git commit -m "gevorgpoghos2 info"

# Перед `push` выполняем `pull` с merge, чтобы избежать линейной истории
git pull server master --no-rebase
git push server master

# Получение последних изменений с сервера
git pull server master --no-rebase

# Последний коммит и пуш исправлений в readme
git add readme.md
git commit -m "readme fix"
git push server master

# Переход к bare-репозиторию и просмотр истории
cd ..
cd server
git log -n 5 --graph --decorate --all
```

