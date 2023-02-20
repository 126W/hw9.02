# Домашнее задание к занятию "`9.2 «Zabbix. Часть 1`" - `Евгений Шахов`
---
### Задание 1

![image](https://user-images.githubusercontent.com/122415129/220200928-425a8fbe-cfc3-45d5-a77b-979c6b1692eb.png)

![image](https://user-images.githubusercontent.com/122415129/220200996-aa0a45a5-9623-4ecb-88bd-1af600f89ba3.png)

![image](https://user-images.githubusercontent.com/122415129/220201227-9e070d68-948a-43c9-a777-739c3d269036.png)

  sudo apt install postgresql  
  wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4%2Bdebian11_all.deb  
  dpkg -i zabbix-release_6.0-4+debian11_all.deb  
  apt update  
  sudo apt install -y zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent  
  su - postgres -c 'psql --command "CREATE USER zabbix WITH PASSWORD '\'123456789\'';"'  
  su - postgres -c 'psql --command "CREATE DATABASE zabbix OWNER zabbix;"'  
  zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix  
  sed -i 's/# DBPassword=/DBPassword=123456789/g' /etc/zabbix/zabbix_server.con  
  sudo systemctl restart zabbix-server zabbix-agent apache2  
  sudo systemctl enable zabbix-server zabbix-agent apache2  
  http://192.168.1.100/zabbix  log:Admin psswd:zabbix  

---
### Задание 2

![image](https://user-images.githubusercontent.com/122415129/220206878-17ee2c75-2a7a-4245-9e37-15befc03b7d3.png)

![image](https://user-images.githubusercontent.com/122415129/220202273-8e606c91-918b-4733-8756-254e13441442.png)

![image](https://user-images.githubusercontent.com/122415129/220207086-724ed098-31a5-41f6-ade2-259b3249091c.png)

wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4%2Bdebian11_all.deb  
dpkg -i zabbix-release_6.0-4+debian11_all.deb  
apt update  
sudo apt install zabbix-agent -y  
sudo systemctl restart zabbix-agent  
sudo systemctl enable zabbix-agent  
nano /etc/zabbix/zabbix-agentd.conf  
192.168.1.100  
sudo systemctl restart zabbix-agent  
sudo systemctl enable zabbix-agent  
sudo systemctl status zabbix-agent  
![image](https://user-images.githubusercontent.com/122415129/220208480-9ccb2951-6d98-4220-8fc8-2abb19c7ef4b.png)

---
