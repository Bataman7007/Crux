# Crux (v3) — PWA prête à héberger et installer sur Android

Ce dossier est la version `Crux-graph-v3.html` transformée en **PWA complète** :
un vrai `manifest.webmanifest`, un `service-worker.js` (cache hors-ligne robuste) et
les icônes en fichiers séparés. Le design n'a pas changé.

## Contenu

| Fichier | Rôle |
|---|---|
| `index.html` | L'app complète (autonome : React, police, code tout inline) |
| `manifest.webmanifest` | Déclaration de l'app installable (nom, icônes, couleurs, plein écran) |
| `service-worker.js` | Cache hors-ligne + rechargement fiable |
| `icons/` | Icônes 192 / 512 / maskable + apple-touch |

## Étape 1 — Mettre en ligne (HTTPS obligatoire pour installer)

Choisis une méthode :

**A. Netlify (le plus simple)**
1. Va sur **https://app.netlify.com/drop** (crée un compte gratuit si demandé).
2. Glisse-dépose **le dossier `crux-v3-pwa`** entier.
3. Tu obtiens une URL `https://…netlify.app`.

**B. GitHub Pages**
1. Crée un dépôt public, téléverse **le contenu** de `crux-v3-pwa` (`index.html` à la racine).
2. Settings → Pages → branche `main`, dossier `/root` → enregistre.
3. URL : `https://<pseudo>.github.io/<repo>/`.

## Étape 2 — Installer sur Android (Chrome)

1. Ouvre l'URL dans **Chrome** sur ton téléphone, laisse charger une fois (mise en cache hors-ligne).
2. Menu **⋮** → **« Installer l'application »** (ou « Ajouter à l'écran d'accueil »).
3. Confirme → l'icône Crux (montagne verte) apparaît, l'app s'ouvre en **plein écran**.

À partir de là, l'app fonctionne **hors-ligne** et tes données restent sur le téléphone
(sauvegarde auto + export/import JSON dans Profil).

## Pourquoi cette version plutôt que le fichier seul ?

Le `Crux-graph-v3.html` seul fonctionne, mais générait son manifest à la volée (Blob),
ce que Chrome n'accepte pas toujours pour proposer une vraie installation. Ici, le
manifest et le service worker sont des **fichiers réels** → installation Android la plus
fiable, icône correcte, et hors-ligne géré par le cache du service worker.

> Rappel : on ne peut pas « installer » un fichier ouvert en local (`file://`) sur Android.
> Il faut passer par une URL HTTPS (étape 1).
