apachelounge.com/download.

* Содержимое скаченного архива (точнее говоря, только каталог Apache24), распакуйте в C:\Server\bin\. 
* Перейдите в каталог c:\Server\bin\Apache24\conf\ и октройте файл httpd.conf 
  Меняем 
  * ServerRoot "c:/Apache24" ->ServerRoot "c:/Server/bin/Apache24"
  *#ServerName www.example.com:80->ServerName localhost
  *DocumentRoot "c:/Apache24/htdocs"->DocumentRoot "c:/Server/data/htdocs/"
  *<Directory "c:/Apache24/htdocs"> -> <Directory "c:/Server/data/htdocs/">
  *DirectoryIndex index.html ->DirectoryIndex index.php index.html index.htm

  *# AllowOverride controls what directives may be placed in .htaccess files.
# It can be "All", "None", or any combination of the keywords:
#   AllowOverride FileInfo AuthConfig Limit
#
AllowOverride None

->
# AllowOverride controls what directives may be placed in .htaccess files.
# It can be "All", "None", or any combination of the keywords:
#   AllowOverride FileInfo AuthConfig Limit
#
AllowOverride All

  *#LoadModule rewrite_module modules/mod_rewrite.so->LoadModule rewrite_module modules/mod_rewrite.so

* Сохраняем и закрываем файл. Всё, настройка Apache завершена! 

* cmd->c:\Server\bin\Apache24\bin\httpd.exe -k install
* c:\Server\bin\Apache24\bin\httpd.exe -k start
