## Zabbix Monitoring Infrastructure

## Step 1: Server Installation
Setting up the Zabbix Server (PHP, Apache, MySQL).

```
wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.0+ubuntu24.04_all.deb
sudo dpkg -i zabbix-release_latest_7.0+ubuntu24.04_all.deb
sudo apt update
```

## Step 2: Server & Frontend Setup
```
sudo apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent
```

## Step 3: Database Configuration 
Importing the initial schema for Zabbix 7.0.
```
zcat /usr/share/zabbix-sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix
```

## Step 4: Docker Monitoring Integration
```
sudo usermod -aG docker zabbix
sudo systemctl restart zabbix-agent
```
<img width="962" height="225" alt="Screenshot 2026-04-21 173633" src="https://github.com/user-attachments/assets/a1873c7a-797c-4c95-bd89-ce773bafebf6" />

## Step 5: Service Management
```
sudo systemctl restart zabbix-server zabbix-agent apache2
sudo systemctl enable zabbix-server zabbix-agent apache2
```

<img width="1600" height="237" alt="Screenshot 2026-04-21 175539" src="https://github.com/user-attachments/assets/27791b86-dd35-41ab-aafc-00c940442301" />
*****
<img width="1868" height="904" alt="Screenshot 2026-04-21 173944" src="https://github.com/user-attachments/assets/b7d60014-ec99-4aa5-adf0-3aabe31032df" />


Author: Max (m-sach-sysadmin)
Platform: Ubuntu 24.04 LTS (Noble)
Stack: Zabbix 7.0 LTS

