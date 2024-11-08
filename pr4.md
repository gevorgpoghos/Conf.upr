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
![Screenshot 2024-11-08 090830](https://github.com/user-attachments/assets/35078ab4-9b12-42ac-9a01-67bb65164450)
![Screenshot 2024-11-08 090947](https://github.com/user-attachments/assets/c689473b-636f-49ce-a71c-85cd78270f41)

```
92604@Matebook-Tema MINGW64 ~
$ mkdir my

92604@Matebook-Tema MINGW64 ~
$ cd my

92604@Matebook-Tema MINGW64 ~/my
$ git init
Initialized empty Git repository in C:/Users/92604/my/.git/

92604@Matebook-Tema MINGW64 ~/my (master)
$ git config user.name "mingazutdinov.a.r"

92604@Matebook-Tema MINGW64 ~/my (master)
$ git config user.email "9260410487am@mail.ru"

92604@Matebook-Tema MINGW64 ~/my (master)
$ nano prog.py

92604@Matebook-Tema MINGW64 ~/my (master)
$ git config --global core.autocrlf false

92604@Matebook-Tema MINGW64 ~/my (master)
$ git add prog.py

92604@Matebook-Tema MINGW64 ~/my (master)
$ git commit -m "Добавление фвйла"
[master (root-commit) c9b348f] Добавление фвйла
 1 file changed, 1 insertion(+)
 create mode 100644 prog.py
```
