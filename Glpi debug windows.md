
### Lancer le .msi en administrateur via PowerShell
Ouvrir **PowerShell en administrateur** (*clic droit → Exécuter en tant qu’administrateur*) puis exécuter :

```powershell
msiexec /i "C:\Users\tonuser\Downloads\glpi-agent-1.15-x64.msi"
```

> ⚠️ **Attention :**
> - Si l’option _Exécuter en tant qu’administrateur_ n’apparaît pas dans l’explorateur Windows, il faut passer par PowerShell.
> - Adapter le chemin du `.msi` si nécessaire.
donc logiquement c'est dans les downloads

---

## Navigation dans le dossier d’installation

```powershell
cd "C:\Program Files\GLPI-Agent"
```

---

## Forcer un inventaire manuel

```powershell
 .\glpi-agent.bat --server http://192.168.1.18/marketplace/glpiinventory/
```
ou mettre les chemin que tu as mis sur l'installer lors de l'installation du msi. 

---

## Redémarrer le service Windows

`Restart-Service glpi-agent`

### Vérifier que le service tourne bien

`Get-Service glpi-agent`

Résultat attendu :

```powershell 
Status   Name               DisplayName ------   ----               ----------- Running  glpi-agent         GLPI Agent`
```
---

## résumé
 
Commande pour lancer le msi en mode admin sur powershelll (en etant déjà en admin)
    `C:\Users\tonuser\Downloads\glpi-agent-1.15-x64.msi`
    
4. Aller dans le bon dossier (toujours necessaire)
    
    `cd "C:\Program Files\GLPI-Agent"`
    
5. Forcer un inventaire

   ```powershell
   .\glpi-agent.bat --server  http://192.168.1.18/marketplace/glpiiventory
    ```
 (ou autre chemin)


important : mettre le bon url si par exemple tu as configuré sur l'installer un autre url met celui que tu as mis 

astuce : mettre plusieurs url lorsque tu fais l'installation avec le .msi, par exemple mettre

```powershell
http://192.168.1.18/glpi, http://192.168.1.18, http://192.168.1.18/marketplace/glpiinventory
```

    
6. Redémarrer le service
    
    `Restart-Service glpi-agent`

---
bien penser a activer l'inventaire dans administration > inventaire et c'est la premiere ligne 
