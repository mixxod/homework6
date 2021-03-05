# Homework6
Homework6_GIT
Задачи:
1. Создать отдельный репозиторий на github.
2. Создать локально три текстовых файла.
3. Поместить в стейдж, закомитить, запушить.
4. Создать две новые ветки.
5. Внести изменения в ветку 1 и 2 
6. Смерджить между собой вновь созданные ветки.
7. Смерджить ветку с веткой мастер
8. Отменить предыдущий комит
9. Все изменения запушить в гит репозиторий.

=======================================================
##
```
Практическая часть:
1.Необходимо представиться ГИТу(делается один раз):
git config --global user.name "mixxod"
git config --global user.email "mixxod@gmail.com"
Создаем рабочий каталог
mkdir mikedevops
Инициализируем GIT
git init
Видем (mc), что пояилась скрытый каталог /.git
Создадим несколько файлов 
root@homework6git:/home/mikekey/mikedevops# echo "first test file" > first.test
root@homework6git:/home/mikekey/mikedevops# echo "second test file" > second.test
root@homework6git:/home/mikekey/mikedevops# echo "therd test file" > therd.test
Проверяем git status
Добавляем git add *
Коммитрим git commit или можно так: git commit -m "My files"
Делаем клон подготовленного репозитория c github
git clone https://github.com/mixxod/Homework6.git
переносим созданные файлы в каталог склонированного репозитория
git push


```
## Создание веток и работа с ними
```
git branch newbranch1
git branch newbranch2
git branch
Видем:
* main
  newbr1
  newbr2
```
## Bнести изменения в ветку 1 и 2
```
Bнести изменения в ветку 1 и 2
Переключимся на ветку
git chechout newbranch1
git status
echo "new text for newbranch1" > fileferst.txt
git add *
git commit
git status
Работа со второй веткой
git checkout newbranch2
echo "new text for newbranch2" > filesecond.txt
git status
git add *
git commit
Посмотрим, что получилось:
git log -n 2 --graph --all
root@homework6git:/home/mikekey/mikedevops/Homework6# git log -n 2 --graph --all
* commit 768a64a9b5b3eb9b90102380ee72ddfa1cbc6915 (HEAD -> newbranch2)
| Author: mixxod <mixxod@mail.com>
| Date:   Fri Mar 5 09:02:49 2021 +0000
|
|     new branch2 and new description
|
| * commit 930cb7abb3fa9fde78125b699f338a9167bf5902 (newbranch1)
|/  Author: mixxod <mixxod@mail.com>
|   Date:   Fri Mar 5 09:00:09 2021 +0000
|
|       add new branck and new description
```

## Смержить две созданные ветки
```
git merge newbranch1 -m "merge newbranch1 >newbranch2"
git log -n 2 --graph --all
root@homework6git:/home/mikekey/mikedevops/Homework6# git log -n 2 --graph --all                                              *   commit c6fe5d69a4a4f143b10a53463dec998e65a2e683 (HEAD -> newbranch2)
|\  Merge: 768a64a 930cb7a
| | Author: mixxod <mixxod@mail.com>
| | Date:   Fri Mar 5 09:18:41 2021 +0000
| |
| |     merge newbranch1 >newbranch2
| |
| * commit 930cb7abb3fa9fde78125b699f338a9167bf5902 (newbranch1)
| | Author: mixxod <mixxod@mail.com>
| | Date:   Fri Mar 5 09:00:09 2021 +0000
| |
| |     add new branck and new description
```

## Смерджить ветку с веткой мастер
```
git checkout main
git branch
git merge newbranch2 -m "merge newbranch2 >main"
git log -n 2 --graph --all
root@homework6git:/home/mikekey/mikedevops/Homework6# git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)
root@homework6git:/home/mikekey/mikedevops/Homework6# git branch
  develop
* main
  newbranch1
  newbranch2
root@homework6git:/home/mikekey/mikedevops/Homework6# git merge newbranch2 -m "merge newbranch                                2 >main"
Updating 1b86dbb..c6fe5d6
Fast-forward (no commit created; -m option ignored)
 fileferst.txt  | 1 +
 filesecond.txt | 1 +
 2 files changed, 2 insertions(+)
 create mode 100644 fileferst.txt
 create mode 100644 filesecond.txt
root@homework6git:/home/mikekey/mikedevops/Homework6# git log -n 2 --graph --all                                             
 *   commit c6fe5d69a4a4f143b10a53463dec998e65a2e683 (HEAD -> main, newbranch2)
|\  Merge: 768a64a 930cb7a
| | Author: mixxod <mixxod@mail.com>
| | Date:   Fri Mar 5 09:18:41 2021 +0000
| |
| |     merge newbranch1 >newbranch2
| |
| * commit 930cb7abb3fa9fde78125b699f338a9167bf5902 (newbranch1)
| | Author: mixxod <mixxod@mail.com>
| | Date:   Fri Mar 5 09:00:09 2021 +0000
| |
| |     add new branck and new description

```

## Отменить предыдущий комит
```
git reset --hard HEAD~1
git log -n 2 --graph --all
root@homework6git:/home/mikekey/mikedevops/Homework6# git reset --hard HEAD~1
HEAD is now at 768a64a new branch2 and new description
root@homework6git:/home/mikekey/mikedevops/Homework6# git log -n 2 --graph --all
*   commit c6fe5d69a4a4f143b10a53463dec998e65a2e683 (newbranch2)
|\  Merge: 768a64a 930cb7a
| | Author: mixxod <mixxod@mail.com>
| | Date:   Fri Mar 5 09:18:41 2021 +0000
| |
| |     merge newbranch1 >newbranch2
| |
| * commit 930cb7abb3fa9fde78125b699f338a9167bf5902 (newbranch1)
| | Author: mixxod <mixxod@mail.com>
| | Date:   Fri Mar 5 09:00:09 2021 +0000
| |
| |     add new branck and new description
```
## Все изменения запушить в гит репозиторий.
git branch (локальный репозиторий)
git branch -r (удаленный репозиторий)

git push -u origin newbrach1 --- загрузка с локального репозитория на удаленный
git push origin --delete develop --- удаление 

