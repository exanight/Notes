⚠️ Ne pas oublier de cliquer sur Activer l’inventaire : administration > inventaire et c'est la première ligne

→ sinon les agents seront refusés.

##### Installation de l’agent GLPI (sur une autre VM Debian)
Télécharger l’agent :
pareil ici toujours vérifier que le lien vers le téléchargement marche : une simple recherche suffit. 

```bash
wget https://github.com/glpi-project/glpi-agent/releases/download/1.15/glpi-agent-1.15-linux-installer.pl -O glpi-agent.pl
sudo perl glpi-agent.pl
```

il demande :
```bash
> Provide an url to configure GLPI server:
 
> http://192.168.1.18 #mets l'IP du serveur

> Provide a path to configure local inventory run or leave it empty:
```

Faites "entrer" et laissez vide.

```bash
Provide a tag to configure or leave it empty: leave empty
```
Faites "entrer" et laissez vide.

Vérifier le service :

```bash
systemctl status glpi-agent
```

⚠️ Si le service ne démarre pas → vérifier perl et les dépendances.

##### Lancer un inventaire
Depuis la machine cliente :

```bash
sudo glpi-agent --server http://192.168.X.X/marketplace/glpiinventory/ --force --debug
```
⚠️ Si erreur 403 Forbidden →
Vérifier que le plugin GLPI Inventory est activé côté serveur.

Vérifier que l’URL est bien :
```bash
http://IP/marketplace/glpiinventory/ #mettez la bonne url.
```