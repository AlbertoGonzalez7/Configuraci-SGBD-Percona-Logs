# CONFIGURACIÓ SGBD
![image](https://user-images.githubusercontent.com/101892290/161306506-ac838ab3-13b9-4da8-93b6-0c3ee962416c.png)
## REALITZA LES SEGÜENTS TASQUES DE CONFIGURACIÓ i COMPROVACIÓ DE LOGS (6 punts)
## --------------------------------------------------------------------------------------------------------

### 1. Quins són els logs activats per defecte?
* *Els logs que venen activats per defecte son el log_bin i el log_error*

> ![1](https://user-images.githubusercontent.com/101892290/161307044-b438418e-9980-492d-98ba-3cc0eaa06e30.jpg)

### Crea un fitxer de configuració anomenat logs.cnf a on:
### Activa els logs que no ho estiguin per defecte i indica les configuracions necessàries per activar-los. Indica les rutes dels fitxer de log de Binary, Slow Query i General. Quins paràmetres has creat/modificat?

* *Crearem l'arxiu logs.cnf i donarem permisos d'escritura a Mysql per que així pugui editar aquest arxiu*

![1 2](https://user-images.githubusercontent.com/101892290/161307979-da86f785-6822-47b5-9fe6-561bb5ec6a03.jpg)

![1 3](https://user-images.githubusercontent.com/101892290/161308036-fe4f3385-1541-4195-9c2b-a71f45c7c8e0.jpg)

* *Comprovació de que te els permisos*

![image](https://user-images.githubusercontent.com/101892290/161308349-4761ef2f-42e2-49b1-a974-096fcdc3b9e5.png)

* *Amb la seguent comanda farem que la configuració del mysql detecti l'arxiu logs.cnf (dintre de my.cnf)*

![image](https://user-images.githubusercontent.com/101892290/161308469-7c6b23ed-6ebb-4916-9fd3-3a714d27bb11.png)

* *En el meu cas, el log_bin ja esta activat, si el volguesim desactivar només hauriem de treue es hashtag (#) devant de disable_log_bin*

![image](https://user-images.githubusercontent.com/101892290/161308880-eeea7515-b03f-4789-9a2d-a450c7aad599.png)

* *Ara anem a la ruta /var/lib/mysql/mysql, i crearem dos fitxers amb el permis de propietari mysql, un per a els logs Slow Query i un altre per els logs de General*

![1 6](https://user-images.githubusercontent.com/101892290/161309417-964eeab6-7dd0-4990-8c0e-8e69b9448f16.jpg)

![1 7](https://user-images.githubusercontent.com/101892290/161309861-2961c8db-e392-43c6-ba77-650cf75dce3e.jpg)

![image](https://user-images.githubusercontent.com/101892290/161309901-572532c3-0a8e-43d8-800d-9d2de9ca6325.png)
![image](https://user-images.githubusercontent.com/101892290/161309685-5ab836d9-ed8f-427e-a85d-3a206f047a1c.png)

![1 8](https://user-images.githubusercontent.com/101892290/161310020-01752bc3-4cbb-40e1-89cd-ca96fdbb973f.jpg)

* *Ara, per activar que els logs, haurem de posar el seguent en l'arxiu logs.cnf, on indicarem la ruta on es guardaran els logs i l'activarem amb un 1 (per desactivar hauríem de posar un 2)*

![1 9](https://user-images.githubusercontent.com/101892290/161310239-e248fa42-be85-4acf-b7d9-93828b00fd7f.jpg)

* *I reiniciem el servei mysqld per veure els canvis*

![1 10](https://user-images.githubusercontent.com/101892290/161310341-3d5ea668-28d2-474a-99eb-c90b209c9e44.jpg)

### 2. Comprova l'estat de les opcions de log que has utilitzat mitjançant una sessió de mysql client.
#### Exemple: (mysql> SHOW GLOBAL VARIABLES LIKE '%log')

* *Podem observar des de el mysql que el slow_query_log i el general_log estan activats*

![2](https://user-images.githubusercontent.com/101892290/161310884-69c1b2e8-52c7-4383-9f78-13aff8e65d58.jpg)

* *També el log_bin que ve per defecte*

![2 2](https://user-images.githubusercontent.com/101892290/161310994-ccf8cf00-6e79-4293-9111-44f64f1b3103.jpg)

### 3. Modifica el fitxer de configuració i desactiva els logs de binary, slow query i genral. Nota: Simplament desactiva'ls no borris altres paràmetres com la ruta dels fitxers, etc...

* *Per desactivar el slow_query_log i el general_log, anirem a l'arxiu logs.cnf i posarem un 2 en el nom del log per desactivarlo.*

![3](https://user-images.githubusercontent.com/101892290/161311190-153345b5-47ab-40fa-aae2-9581bcfacd7b.jpg)

* *Per desactivar el log_bin haurem de treure el hashtag (#) a disable_log_bin dintre de /my.cnf*

![3 1](https://user-images.githubusercontent.com/101892290/161311291-5db087b0-8bc9-4f8d-beee-4ff03bef74ad.jpg)

* *Reiniciem per guardar els canvis*

![3 2](https://user-images.githubusercontent.com/101892290/161311370-073aa42e-54f0-4e66-bb76-ac3a1a584fc7.jpg)

* *I així desactivarem els logs*

![3 3](https://user-images.githubusercontent.com/101892290/161311423-8398c4aa-3075-4eda-b1d7-4d250780c9c1.jpg)

![3 4](https://user-images.githubusercontent.com/101892290/161311435-9d5ef576-6571-42f7-883f-71950f5645cc.jpg)

### 4. Activa els logs en temps d'execució mitjançant la sentència SET GLOBAL. També canvia el destí de log general a una taula (paràmetre log_output). Quines són les sentències que has utilitzat? A quina taula es guarden els dels del general log?

* *Executem la comanda SET GLOBAL general_log = 'ON'; al Mysql per activar el general log, que ja ve creada la taula*

![4](https://user-images.githubusercontent.com/101892290/161311844-73868e37-3b40-4794-ac6a-1f17ad45e192.jpg)

![4 1](https://user-images.githubusercontent.com/101892290/161311864-54dcb4b5-de56-4d00-8d0b-e448af1a256b.jpg)

* *Executarem la comanda SET GLOBAL log_output = 'table'; per guardar els logs en format de taula*

![4 2](https://user-images.githubusercontent.com/101892290/161312027-76575b52-e041-4c6d-bc0f-f94aa8fe424f.jpg)

### 5. Carrega la BD Sakila localitzada a la web de o Descarrega't el fitxer sakila-schema.sql del Moodle. o carrega la BD dins del MySQL utilitzant la sentència: 
#### mysql> SOURCE <ruta_fitxer>/sakila-schema.sql;

* *Descarragarem la base de dades amb el seguent enllaç*

* https://dev.mysql.com/doc/index-other.html

* *Amb el programa (WinSCP) Pasarem el sakila-schema a la nostra maquina virtual en la ruta /var/lib/mysql/mysql*

![image](https://user-images.githubusercontent.com/101892290/161312600-723517d5-342d-46f9-bc1e-4073813768ce.png)

* *I la carregarem amb la seguent comanda*

![5](https://user-images.githubusercontent.com/101892290/161312716-65fbb0e4-4e29-47c3-9f0c-38d03f580179.jpg)

* *I com podem observar, ja la tindirem*

![5 1](https://user-images.githubusercontent.com/101892290/161312757-b9ee4f0c-48cd-4212-9b32-2d91d35f4fe5.jpg)

### 6. Compte el numero de sentències CREATE TABLE dins del general log mitjançant una sentència SQL. o Mostra quina sentència has utilitzat i mostra'n el resultat.

* *Per comptar el numero de sentències es fa amb la comanda SELECT COUNT( * ) FROM gemeral_log argument LIKE 'CREATE TABLE%'; al Mysql, pero ens surt 0, això es degut perque l'argument es troba en sistema Hexadecimal i l'hem de transformar a string*

![image](https://user-images.githubusercontent.com/101892290/161313555-78ba46b7-d9ca-45ff-a741-dd2017242bb4.png)

* *Per poder passar de Hexadecimal a string ho hem de fer amb les seguents comandes:*

![image](https://user-images.githubusercontent.com/101892290/161313766-4bd294cf-d97a-411f-85d4-268f24c86526.png)

* *I així ens sortirà en el COUNT( * ) el número 16, que és el número de taules que te la bd sakila*

### 7. Executa una query mitjançant la funció SLEEP(11) per tal de que es guardi en el log de Slow Query Log. Mostra el contingut del log demostrant-ho.

* *Executem una query amb la comanda SELECT SLEEP(11): al Mysql*

![7](https://user-images.githubusercontent.com/101892290/161314117-e386cd98-e19a-44c1-9c2f-c292f358d169.jpg)

* *I en el contingut del Slow Query log, ens surt la comanda*

![7 1](https://user-images.githubusercontent.com/101892290/161314239-e042fdf2-75f9-484c-8b13-e14206735727.jpg)

### 8. Assegura't que el Binary Log estigui activat i borra tots els logs anteriors mitjançant la sentència RESET MASTER.

* *Fem la comanda RESET MASTER; i comprovem que el Binary Log està activat*

![8](https://user-images.githubusercontent.com/101892290/161314504-361d9dcc-6167-4963-90e3-05f89f2ee776.jpg)






