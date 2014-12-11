# Php: FastCGI, CGI et mod_php
Les différences entre CGI, Fast CGI et mod_php
Quelle est la particularité de Php ?

Voici un [site](http://blog.layershift.com/which-php-mode-apache-vs-cgi-vs-fastcgi/) qui détaille les différences

En gros, ça donne ça *(d'après ce [comparatif](http://boomshadow.net/tech/php-handlers/))*

|DSO|CGI|SuPHP|FastCGI|
|---|---|-----|-------|
|Low CPU usage|✔|||✔|
|Low Memory consumption|✔|✔|✔||
|Runs PHP as site owner instead of Apache||✔only w/ suEXEC|✔|✔|
|Good security|||✔|✔|
