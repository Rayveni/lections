apachelounge.com/download.

* ���������� ���������� ������ (������ ������, ������ ������� Apache24), ���������� � C:\Server\bin\. 
* ��������� � ������� c:\Server\bin\Apache24\conf\ � �������� ���� httpd.conf 
  ������ 
  * ServerRoot "c:/Apache24" ->ServerRoot "c:/Server/bin/Apache24"
  *#ServerName www.example.com:80->ServerName localhost
  *DocumentRoot "c:/Apache24/htdocs"->DocumentRoot "c:/Server/data/htdocs/"
  *<Directory "c:/Apache24/htdocs"> -> <Directory "c:/Server/data/htdocs/">
  *DirectoryIndex index.html ->DirectoryIndex index.php index.html index.htm

  *# AllowOverride controls what directives may be placed in .htaccess files.
# It can be "All", "None", or any combination of the keywords:
#�� AllowOverride FileInfo AuthConfig Limit
#
AllowOverride None

->
# AllowOverride controls what directives may be placed in .htaccess files.
# It can be "All", "None", or any combination of the keywords:
#�� AllowOverride FileInfo AuthConfig Limit
#
AllowOverride All

  *#LoadModule rewrite_module modules/mod_rewrite.so->LoadModule rewrite_module modules/mod_rewrite.so

* ��������� � ��������� ����. ��, ��������� Apache ���������! 

* cmd->c:\Server\bin\Apache24\bin\httpd.exe -k install
* c:\Server\bin\Apache24\bin\httpd.exe -k start
