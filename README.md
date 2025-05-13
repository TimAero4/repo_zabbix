# repo_zabbix

#<ins>Команды для установки Zabbix Server</ins>

## sudo -s
## установка СУБД
## apt install postgresql
## wget https://repo.zabbix.com/zabbix/7.2/release/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.2+ubuntu22.04_all.deb
## dpkg -i zabbix-release_latest_7.2+ubuntu22.04_all.deb
## ls -al /etc/apt/sources.list.d/
## cat /etc/apt/sources.list.d/zabbix.list
## среди ZABBIX MAIN REPOSITORY выбираем
## apt update
## apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
## systemctl status zabbix-server.service
## su - postgres -c 'psql --command "CREATE USER zabbix WITH PASSWORD '\'123456789\'';"'
## su - postgres -c 'psql --command "CREATE DATABASE zabbix OWNER zabbix;"'
## импортирование первичных скриптов
## find / -name zabbix_server.conf
## nano /etc/zabbix/zabbix_server.conf
## systemctl restart zabbix-server apache2
## systemctl enable zabbix-server apache2
## systemctl status zabbix-server apache2
## ip a -> 10.0.2.15
## http://10.0.2.15/zabbix
[autorization](image/autorize.png)
[main_page](image/first_page.png)

#<ins>Команды для установки Zabbix Agent</ins>

## sudo -s
## установка СУБД
## apt install
## установка репозитория
## wget https://repo.zabbix.com/zabbix/7.2/release/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.2+ubuntu22.04_all.deb
## dpkg -i zabbix-release_latest_7.2+ubuntu22.04_all.deb
## ls -al /etc/apt/sources.list.d/
## cat /etc/apt/sources.list.d/zabbix.list
## apt install zabbix-agent
## systemctl restart zabbix-agent
## systemctl enable zabbix-agent

#<ins>Постановка хоста с Zabbix agent на мониторинг</ins>
## Добавляем основную информацию (адрес, днс) о хосте,где находится агент(в веб интерфейсе заббикс сервера).
## nano /etc/zabbix/zabbix_agentd.conf в файле меняем Server=ipv4
## systemctl restart/status zabbix-agent
## tail -f /var/log/zabbix/zabbix_agentd.log (в результате видим, что подключения нету)
[hosts](image/hosts.png)
[monitoring](image/latest.png)
