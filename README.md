# 🦜 Perroquitos

Une petite application web (PWA) de soundboard : chaque bouton rejoue un son que tu as enregistré ou importé, avec un emoji pour le reconnaître. Tout est stocké sur ton téléphone, sans compte ni serveur.

**Application : https://a-rech.github.io/monperroquet/**

## Fonctionnalités

- Enregistrement au micro ou import d’un fichier audio (mp3, wav, m4a, ogg…)
- Éditeur d’extrait : choix du début et de la fin sur la forme d’onde, avec écoute avant de valider
- Un emoji, un nom, un volume et une catégorie par bouton
- Catégories colorées, avec onglets pour filtrer
- Mode édition (✏️) : glisser-déposer pour réorganiser, toucher un bouton pour le modifier
- Comportement quand on touche un bouton déjà en lecture, au choix : rejouer, arrêter ou superposer
- Nombre de colonnes réglable
- Volume général, fondus d’entrée et de sortie par son, vibration au toucher
- Boutons sans son : un appui propose d’en ajouter un
- Partage d’un extrait vers une autre appli Android (fichier .wav)
- Fonctionne hors ligne une fois installée

## Installation

1. Ouvrir l’adresse ci-dessus dans Chrome sur Android.
2. Menu ⋮ puis « Installer l’application » (ou « Ajouter à l’écran d’accueil »).

## Sauvegardes

Les sons sont stockés dans IndexedDB, dans le navigateur de l’appareil. Cela signifie que **effacer les données du site ou désinstaller le navigateur supprime les sons**. Pour ne rien perdre :

- **Exporter (.json)** : réglages ⚙️, puis « Exporter ». Le fichier contient tous les sons et catégories. À conserver hors du téléphone (cloud, ordinateur).
- **Exporter une catégorie** : même principe, pour une seule catégorie.
- **Importer** : fusionne un fichier exporté avec les sons déjà présents.
- **Sauvegarde interne** : une seule copie, stockée dans le navigateur, qui remplace la précédente à chaque fois. Pratique pour revenir en arrière, mais elle ne protège pas contre un effacement des données du site.
- Un bandeau de rappel apparaît si le dernier export date de plus de 14 jours.

## Déploiement

Le projet est statique : il suffit de pousser les fichiers à la racine du dépôt et d’activer GitHub Pages (Settings → Pages → branche `main`, dossier `/ (root)`).

| Fichier | Rôle |
|---|---|
| `index.html` | Toute l’application (HTML, CSS, JS) |
| `manifest.json` | Nom, couleurs et icônes de l’app installée |
| `sw.js` | Service worker pour le mode hors ligne |
| `icon-192.png`, `icon-512.png` | Icônes |

Après une modification, change le numéro de version du cache dans `sw.js` (`sb-v4`, `sb-v5`…) pour que les appareils déjà installés récupèrent la mise à jour.

## Technique

JavaScript natif, sans framework ni dépendance. Audio via Web Audio API et MediaRecorder, stockage via IndexedDB.

L’emoji des icônes est le perroquet de Noto Emoji (Google), distribué sous licence Apache 2.0.
