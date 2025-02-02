# Pipeline CI/CD pour le projet HTML/CSS

Ce document décrit les étapes de l'intégration continue (CI) et du déploiement/livraison continue (CD) pour ce projet.

Michael YAROMISHYAN et 
Kylian DELEY

## Intégration Continue (CI)

### Description

Le pipeline CI vérifie automatiquement le code soumis dans les Pull Requests (PR) en effectuant les étapes suivantes :

- Téléchargement du code depuis le dépôt.
- Installation des dépendances nécessaires.
- Compilation des fichiers CSS (Sass et PostCSS).

### Étapes locales

Pour reproduire le processus CI localement, exécutez :

#### Installer les dépendances
```sh
npm install
```

#### Construire les fichiers CSS
```sh
npm run build
```

---

## Déploiement/Livraison Continue (CD)

### Description

Le pipeline CD est déclenché automatiquement lorsqu'un tag Git correspondant au format `v*` est poussé. Il :

- Génère un livrable (`final.css`).
- Crée une release GitHub associée au tag.
- Attache le fichier `final.css` en tant qu'asset à la release.

### Livrables

- `final.css` : fichier CSS compilé prêt à l'emploi.

### Étapes pour déclencher une livraison

Créez un tag Git :

```sh
git tag v1.0.0
git push origin v1.0.0
```

Vérifiez la release sur GitHub dans l'onglet **Releases**.

---

## Cycle de vie CI/CD

### Développement

1. Les développeurs travaillent sur des branches de fonctionnalités et soumettent des Pull Requests.
2. Le pipeline CI s'exécute pour valider les modifications.

### Mise en production

1. Une fois validé, le code est fusionné dans la branche `main`.
2. Un tag est créé pour déclencher le CD.

### Livraison

- Une nouvelle release GitHub est générée avec les fichiers compilés.