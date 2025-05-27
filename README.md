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
  Écrire à l’intérieur : Que la force soit avec toi.

Déplacement des fichiers avec :
```
mv /home/laplateforme/mon_texte1.txt /home/laplateforme/Bureau
```
Recherche de fichiers contenant un mot :
```
grep -rl "force" ~
```
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
## Manipulation de texte avec Python et awk

Création d’un script Python :
