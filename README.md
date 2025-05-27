# Projet - VM Debian & Commandes Linux

Ce projet résume plusieurs manipulations basiques et avancées sur une machine virtuelle Debian. Il aborde la gestion de fichiers, la compression, les scripts shell/Python, la surveillance système, et l'automatisation.

---

## Création d’une VM Debian & Commandes de base

- Installation d'une VM Debian en interface graphique.
- Création de fichiers texte avec :

  ```
  touch mon_texte.txt
  nano mon_texte.txt
  ```
- Écrire à l’intérieur : Que la force soit avec toi.

Déplacement des fichiers avec :

```
mv /home/laplateforme/mon_texte1.txt /home/laplateforme/Bureau
```
Recherche de fichiers contenant un mot :

```
grep -rl "force" ~
```

---

## Compression et décompression

Création du dossier Plateforme :

```
mkdir ~/Documents/Plateforme
```
Déplacement du fichier texte dans ce dossier :

```
mv mon_texte.txt ~/Documents/Plateforme
```
Duplication pour avoir 5 fichiers :

```
cp mon_texte.txt mon_texte2.txt
cp mon_texte.txt mon_texte3.txt
cp mon_texte.txt mon_texte4.txt
cp mon_texte.txt mon_texte5.txt
```
Compression :

```
cd ~/Documents
tar -czf Plateforme.tar.gz Plateforme
```
Décompression (hors du dossier d’origine) :
```
tar -xzf Plateforme.tar.gz
```

---

## Manipulation de texte avec Python et awk

Création d’un script Python :

<img src="/screen/2.png" alt="Capture d'écran"/>

Exécution :

```
python3 nom_du_fichier.py
```

Extraction des villes :

```
awk -F',' 'NR>1 {print $3}' new_list.csv
```

---

## Gestion des processus

Affichage :

```
ps aux
top
sudo apt install htop
htop
```
Identifier le PID puis :

```
kill <PID>        # Envoie SIGTERM (15)
kill -9 <PID>     # Envoie SIGKILL (9) - Forcé
```

---

## Surveillance des ressources système

Tri par consommation mémoire et export :

```
ps aux --sort -%mem | paste -d ' ' > running_processes.csv
```

---

## Scripting avancé : Sauvegarde automatique

Création du script :

```
nano sauvegarde_plateforme.sh
```

<img src="/screen/3.png" alt="Capture d'écran"/>

Rendre exécutable :

```
chmod +x sauvegarde_plateforme.sh
./sauvegarde_plateforme.sh
```

Automatiser avec cron :

```
crontab -e
# Ajouter :
0 2 * * * /home/laplateforme/sauvegarde_plateforme.sh
```

---

## Automatisation des mises à jour

Création du script :

```
nano mise_a_jour.sh
```

<img src="/screen/4.png" alt="Capture d'écran"/>

On l'exécute :

```
chmod +x mise_a_jour.sh
./mise_a_jour.sh
```

Le script doit permettre à l'utilisateur de choisir s’il veut lancer la mise à jour.

---

## Script d’installation d’un environnement web

```
nano install_web_env.sh
```

<img src="/screen/5.png" alt="Capture d'écran"/>
<img src="/screen/6.png" alt="Capture d'écran"/>

Le script doit :

- Installer les logiciels nécessaires
- Vérifier s’ils sont déjà installés
- Éviter les conflits de version

Et dans le cas où  l’on veut tenir compte du fait que ces logiciels soient installés ou pas, on peut procéder avec les conditions :

<img src="/screen/7.png" alt="Capture d'écran"/>

Exécution :

```
chmod +x install_web_env.sh
./install_web_env.sh
```

---

## Sécurisation des scripts

Risques à éviter :

- Suppression accidentelle de fichiers
- Droits d’accès excessifs (sudo abusif)
- Injection de commande (données non filtrées)
- Fichiers sensibles exposés (ex : mots de passe en clair)

Sécurisation possible :

- Vérifier les entrées utilisateur
- Protéger les mots de passe
- Éviter les commandes critiques sans confirmation

Exemple de sécurisation pour un script créé précédemment :

<img src="/screen/8.png" alt="Capture d'écran"/>

---

## Utilisation d’API Web dans un script

```
nano meteo.sh
```

<img src="/screen/9.png" alt="Capture d'écran"/>

Installer curl si nécessaire :

```
sudo apt install curl
```

Rendre exécutable et exécuter :

```
chmod +x meteo.sh
./meteo.sh
```

<img src="/screen/10.png" alt="Capture d'écran"/>

Qu’est-ce que le Logging (journalisation) ?
Le logging est l’enregistrement des actions d’un script dans un fichier.

Utilité :

- Suivi des erreurs et bugs
- Traçabilité des actions
- Détection des comportements suspects (cybersécurité)
