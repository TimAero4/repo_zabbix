# <ins>repo_zabbix</ins>

# <ins>Команды для установки Zabbix Server</ins>

1. sudo -s
## установка СУБД
2. apt install postgresql
3. wget https://repo.zabbix.com/zabbix/7.2/release/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.2+ubuntu22.04_all.deb
4. dpkg -i zabbix-release_latest_7.2+ubuntu22.04_all.deb
5. ls -al /etc/apt/sources.list.d/
6. cat /etc/apt/sources.list.d/zabbix.list
## среди ZABBIX MAIN REPOSITORY выбираем
7. apt update
8. apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
9. systemctl status zabbix-server.service
10. su - postgres -c 'psql --command "CREATE USER zabbix WITH PASSWORD '\'123456789\'';"'
11. su - postgres -c 'psql --command "CREATE DATABASE zabbix OWNER zabbix;"'
## импортирование первичных скриптов
12. find / -name zabbix_server.conf
13. nano /etc/zabbix/zabbix_server.conf
14. systemctl restart zabbix-server apache2
15. systemctl enable zabbix-server apache2
16. systemctl status zabbix-server apache2
17. ip a -> 10.0.2.15
18.  http://10.0.2.15/zabbix
* [autorization](image/autorize.png)
* [main_page](image/first_page.png)

# <ins>Команды для установки Zabbix Agent</ins>

1. sudo -s
## установка СУБД
2. apt install
## установка репозитория
3. wget https://repo.zabbix.com/zabbix/7.2/release/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.2+ubuntu22.04_all.deb
4. dpkg -i zabbix-release_latest_7.2+ubuntu22.04_all.deb
5. ls -al /etc/apt/sources.list.d/
6. cat /etc/apt/sources.list.d/zabbix.list
7. apt install zabbix-agent
8. systemctl restart zabbix-agent
9. systemctl enable zabbix-agent

# <ins>Постановка хоста с Zabbix agent на мониторинг</ins>
## Добавляем основную информацию (адрес, днс) о хосте,где находится агент(в веб интерфейсе заббикс сервера).
1. nano /etc/zabbix/zabbix_agentd.conf в файле меняем Server=ipv4
2. systemctl restart/status zabbix-agent
3. tail -f /var/log/zabbix/zabbix_agentd.log (в результате видим, что подключения нету)
* [hosts](image/hosts.png)
* [monitoring](image/latest.png)
