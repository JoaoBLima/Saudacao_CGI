# Saudacao_CGI
Passo a Passo para Configuração
1. Instalar o Apache
Se o Apache ainda não estiver instalado, execute os comandos abaixo:

sudo apt update
sudo apt install apache2
2. Habilitar o Módulo CGI no Apache
Para que o Apache suporte scripts CGI, é necessário habilitar o módulo mod_cgi:

sudo a2enmod cgi
Em seguida, reinicie o Apache para aplicar as alterações:

sudo systemctl restart apache2
3. Configurar o Diretório para Scripts CGI
Por padrão, o Apache usa o diretório /usr/lib/cgi-bin/ para scripts CGI. Edite o arquivo de configuração do Apache para garantir que este diretório esteja configurado corretamente:

sudo nano /etc/apache2/sites-available/000-default.conf
No arquivo, adicione a linha abaixo dentro do bloco <VirtualHost>:

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
4. Permitir Execução de CGI no Diretório
Ainda no arquivo de configuração, defina as permissões para que o Apache possa executar scripts CGI dentro do diretório:

<Directory "/usr/lib/cgi-bin">
    Options +ExecCGI
    AddHandler cgi-script .cgi .pl .sh
    Require all granted
</Directory>
