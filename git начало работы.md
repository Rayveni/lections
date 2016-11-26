#Git начало работы

![samumonkey.jpg](G:Git\blog\Images\gitcat.jpg)
https://github.com/
Зачем нужен гит?В первую очередь для командной разработки за счёт поддержки версий (есои в какой то момент ваш проект стал "нестабилен" есть возможность откатиться к стабильной версии).
Лично я использую гит как хранилище своих мини проектов и markdown файлов блога(я в курсе что на гите можно поднять свой блог/сайт причем бесплатно,но настраивать мне это лень)

Регистрируемся, создаем репозитории.
В настройках создаем ключ для работы с помощью api.
(settings->Developer setting->Personal access tokens)

Работать с Git с помощью sh консоли или GUI неспортивно.Настроим python notebook для работы с Git один раз и забудем=)
####Настраиваем python
<code>
!pip install GitPython #мэджик команда для jupyter nootebook
from git import Repo
import os
from os import path
from shutil import copyfile
\#моя функция для визулизации файлов (достаточно FileTreeMaker.py положить в папку с ноутбуком)
from  FileTreeMaker import FileTreeMaker 
\#"┃ ""┣━""┗━"'  '

\#Создаем папку под репозиторий
my_repo_folder='G:\Git'
os.mkdir(my_repo_folder)

\#клонируем интересующий репозиторий в папку
git_url='https://github.com/Rayveni/PY.git'
Repo.clone_from(git_url, my_repo_folder)
\#визуализируем
FileTreeMaker(my_repo_folder,['.git']) #['.git] убирает из дерева папку гит(в ней ничего интересного нет)

\#добавляем новые файлы и папки для последующего коммита на примере этого ноутбука
new_folder=path.join(my_repo_folder,'Utilities')
os.mkdir(new_folder)
notebook_folder=os.environ['USERPROFILE']
copyfile(path.join(notebook_folder,'FileTreeMaker.py'),path.join(new_folder,'FileTreeMaker.py'))
copyfile(path.join(notebook_folder,'Git.ipynb'),path.join(new_folder,'Git.ipynb'))
FileTreeMaker(my_repo_folder,['.git'])
repo = Repo(my_repo_folder)
repo.git.add(new_folder)
repo.git.commit( m='add git ipynb' )
repo.git.status()
with open(path.join(notebook_folder,'git_token.txt'), 'r') as f:
    token=f.read()   #считываю токен для авторизации
repo.git.push('https://'+token+'@github.com/Rayveni/PY.git') #загружаю на гит внесенные правки
<code>
notebook и FileTreeMaker.py можно скачать здесь:https://github.com/Rayveni/PY/tree/master/Utilities