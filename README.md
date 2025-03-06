# lab02
> nano ~/.zshrc
> echo ${GITHUB_TOKEN}

> echo ${GITHUB_EMAIL}
matveech99@gmail.com
> echo ${GITHUB_USERNAME}
matveech99
> alias edit=vi
> cd ${GITHUB_USERNAME}/workspace


> cd ${GITHUB_USERNAME}/workspace
> source scripts/activate
> mkdir ~/.config
mkdir: невозможно создать каталог «/home/matvey/.config»: Файл существует
> cat > ~/.config/hub <<EOF
github.com:
- user: ${GITHUB_USERNAME}
  oauth_token: ${GITHUB_TOKEN}
  protocol: https
EOF


> git config --global hub.protocol https
> mkdir projects/lab02 && cd projects/lab02
> git init
подсказка: Using 'master' as the name for the initial branch. This default branch name
подсказка: is subject to change. To configure the initial branch name to use in all
подсказка: of your new repositories, which will suppress this warning, call:
подсказка: 
подсказка: 	git config --global init.defaultBranch <name>
подсказка: 
подсказка: Names commonly chosen instead of 'master' are 'main', 'trunk' and
подсказка: 'development'. The just-created branch can be renamed via this command:
подсказка: 
подсказка: 	git branch -m <name>
Инициализирован пустой репозиторий Git в /home/matvey/matveech99/workspace/projects/lab02/.git/


> git config --global user.name ${GITHUB_USERNAME}
> git config --global user.email ${GITHUB_EMAIL}
> git config -e --global

[user]
        name = matveech99
        email = matveech99@gmail.com
[credential]
        helper = store
[hub]
        protocol = https


> touch README.md
~/m/w/projects/lab02 master ?1 >  




> git status
Текущая ветка: master

Еще нет коммитов

Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	README.md

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)





> git add README.md
> ~/m/w/p/lab02 master +1 >   




> git status
Текущая ветка: master

Еще нет коммитов

Изменения, которые будут включены в коммит:
  (используйте «git rm --cached <файл>...», чтобы убрать из индекса)
	новый файл:    README.md

~/m/w/projects/lab02 master +1 >  



> git commit -m"added README.md"
[master (корневой коммит) 01abdad] added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
~/m/w/projects/lab02 master >       




> git pull origin master
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Распаковка объектов: 100% (3/3), 979 байтов | 979.00 КиБ/с, готово.
Из https://github.com/matveech99/lab02
 * branch            master     -> FETCH_HEAD
   ea18dee..cad5597  master     -> origin/master
Обновление ea18dee..cad5597
Fast-forward
 .gitignore | 4 ++++
 1 file changed, 4 insertions(+)
 create mode 100644 .gitignore
~/m/w/projects/lab02 master >      






>git log
commit cad5597f87d13fbce4430a9cb270196c039c295a (HEAD -> master, origin/master)
Author: matveech99 <matveech99@gmail.com>
Date:   Thu Mar 6 21:44:01 2025 +0300

    Create .gitignore

commit ea18deef1c831ac246f0cff3556534e150ad6d69
Author: matveech99 <matveech99@gmail.com>
Date:   Thu Mar 6 20:59:07 2025 +0300

    Initial commit
(END)

