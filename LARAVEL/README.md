#Response headers server name and version should not show(laravel)

#Install mod_security
Steps

1 Install mod_security:

```sh
sudo apt-get install libapache2-mod-security2
```
2 Open or create the mod_security configuration file:
```sh
sudo nano /etc/apache2/mods-available/security2.conf
```
3 Add the following configuration:
```sh
<IfModule security2_module>
  SecRuleEngine On
  SecServerSignature " "
</IfModule>
```
4 Enable the mod_security module:
```sh
sudo a2enmod security2
```
 5 Restart Apache:
 ```sh
service apache2 reload
```
After these steps, the Server tag will be empty.
