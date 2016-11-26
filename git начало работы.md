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
!pip install GitPython #мэджик команда для jupyter nootebook<br>
from git import Repo<br>
import os<br>
from os import path<br>
from shutil import copyfile<br>
\#моя функция для визулизации файлов (достаточно FileTreeMaker.py положить в папку с ноутбуком)<br>
from  FileTreeMaker import FileTreeMaker <br>
\#"┃ ""┣━""┗━"'  '<br>

\#Создаем папку под репозиторий<br>
my_repo_folder='G:\Git'<br>
os.mkdir(my_repo_folder)<br>

\#клонируем интересующий репозиторий в папку<br>
git_url='https://github.com/Rayveni/PY.git'<br>
Repo.clone_from(git_url, my_repo_folder)<br>
\#визуализируем<br>
FileTreeMaker(my_repo_folder,['.git']) #['.git] убирает из дерева папку гит(в ней ничего интересного нет)<br>

\#добавляем новые файлы и папки для последующего коммита на примере этого ноутбука<br>
new_folder=path.join(my_repo_folder,'Utilities')<br>
os.mkdir(new_folder)<br>
notebook_folder=os.environ['USERPROFILE']<br>
copyfile(path.join(notebook_folder,'FileTreeMaker.py'),path.join(new_folder,'FileTreeMaker.py'))<br>
copyfile(path.join(notebook_folder,'Git.ipynb'),path.join(new_folder,'Git.ipynb'))<br>
FileTreeMaker(my_repo_folder,['.git'])<br>
repo = Repo(my_repo_folder)<br>
repo.git.add(new_folder)<br>
repo.git.commit( m='add git ipynb' )<br>
repo.git.status()<br>
with open(path.join(notebook_folder,'git_token.txt'), 'r') as f:<br>
    token=f.read()   #считываю токен для авторизации<br>
repo.git.push('https://'+token+'@github.com/Rayveni/PY.git') #загружаю на гит внесенные правки<br>
<code><br>
notebook и FileTreeMaker.py можно скачать здесь:https://github.com/Rayveni/PY/tree/master/Utilities<br>