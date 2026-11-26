# TP – Découverte de Bootstrap 

**Public :** ingénieurs 2ᵉ année, spécialité Technologies Innovantes en Santé (TIS)
**Durée :** 2 heures
**Outils :** un éditeur de code (VS Code conseillé), un navigateur (Chrome, Edge ou Firefox), une connexion Internet

## Contexte

Vous construisez la page web d'un dossier patient : identité, dernières constantes vitales, historique des mesures et formulaire de saisie d'une nouvelle mesure. Le contenu et la structure HTML de la page sont déjà écrits dans le fichier de départ : **votre travail consiste à mettre en forme la page avec Bootstrap**, en ajoutant des classes et quelques balises, sans écrire une seule ligne de CSS.

> ⚠️ Le patient (Yassine Trabelsi) et toutes les valeurs sont **fictifs**. Les statuts « Normal », « À surveiller » et « Alerte » sont illustratifs et n'ont aucune valeur médicale. En situation réelle, on ne manipule jamais de données de patients sans cadre réglementaire et sans anonymisation.

## Objectifs

À la fin du TP, vous savez :

1. intégrer Bootstrap dans une page HTML via un CDN et vérifier qu'il se charge sans erreur ;
2. construire une **navbar** responsive ;
3. organiser une page avec la **grille** (`container`, `row`, `col-*`) et des **cards** ;
4. mettre en forme un **tableau** et signaler visuellement les valeurs anormales ;
5. construire un **formulaire** propre avec les classes Bootstrap ;
6. utiliser les **utilities** (badges, espacements, ombres, alignements).

## Récupérer les fichiers

Ouvrez le dossier `starter/` : il contient `index.html` (à compléter) et `reponses.md` (vos réponses aux questions). Pour travailler, téléchargez le dépôt (**Code → Download ZIP**) ou clonez-le, puis ouvrez le dossier `starter/` dans votre éditeur.

Ouvrez `index.html` dans le navigateur : la page est lisible mais sans aucune mise en forme. Le but est de la transformer. Les commentaires `<!-- ÉTAPE n : … -->` indiquent où intervenir.

## Astuces pour taper moins

- **Ctrl + D** (VS Code) sélectionne l'occurrence suivante du mot sélectionné ; **Ctrl + Maj + L** sélectionne toutes les occurrences. Vous pouvez ainsi ajouter une même classe à tous les `<li>` en une seule fois.
- **Alt + clic** ajoute un curseur supplémentaire.
- Dans le navigateur, **F12** ouvre les outils de développement : onglet *Console* pour les erreurs, et mode appareil mobile (**Ctrl + Maj + M**) pour tester le responsive.
- Toutes les classes dont vous avez besoin sont dans la [documentation Bootstrap 5.3](https://getbootstrap.com/docs/5.3/).

---

## Étape 1 – Mise en place (10 min)

1. Dans `index.html`, ajoutez le `<link>` du **CSS** de Bootstrap à l'endroit indiqué dans le `<head>`, et le `<script>` du **JavaScript** (version *bundle*) juste avant `</body>`. Copiez-les depuis la page [Get started with Bootstrap](https://getbootstrap.com/docs/5.3/getting-started/introduction/), rubrique *Quick start*.
2. Rechargez la page : la typographie doit changer.
3. Ouvrez la console (F12) et vérifiez qu'il n'y a **aucune erreur réseau** (rien en rouge).

**Questions** (à compléter dans `reponses.md`) :

1. Pourquoi faut-il copier le code d'intégration depuis la documentation officielle ?
2. À quoi servent les attributs `integrity=` et `crossorigin="anonymous"` ?

## Étape 2 – Navbar (10 min)

Transformez le bloc `<nav>` en barre de navigation Bootstrap. Voici la structure à obtenir, à adapter à vos liens existants :

```html
<nav class="navbar navbar-expand-md bg-dark" data-bs-theme="dark">
  <div class="container">
    <a class="navbar-brand" href="#">Dossier patient</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
            data-bs-target="#menuPrincipal" aria-controls="menuPrincipal"
            aria-expanded="false" aria-label="Afficher ou masquer le menu">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="menuPrincipal">
      <ul class="navbar-nav me-auto">
        <li class="nav-item"><a class="nav-link" href="#identite">Identité</a></li>
        <!-- … les autres liens -->
      </ul>
    </div>
  </div>
</nav>
```

**À faire :** reprenez vos 4 liens (Identité, Constantes, Historique, Nouvelle mesure) dans cette structure, puis testez en réduisant la fenêtre : le menu doit se replier derrière un bouton « burger ».

Documentation : [Navbar](https://getbootstrap.com/docs/5.3/components/navbar/)

## Étape 3 – Grille et cards (20 min)

**À faire :**

1. Ajoutez la classe `container` sur `<main>`.
2. Sur le `<div>` qui contient les deux sections *Identité* et *Dernières constantes* : ajoutez `row` et `g-4` (espacement entre colonnes).
3. Sur chacune des deux `<section>` : ajoutez `col-12 col-md-6` (pleine largeur sur mobile, moitié de largeur à partir de 768 px).
4. Dans chaque section, transformez le `<div>` interne en **card** (`card h-100`), le `<h2>` en en-tête de card (`card-header`), et la liste `<ul>` en liste de card (`list-group list-group-flush`, avec `list-group-item` sur chaque `<li>`).

Résultat attendu : deux cards côte à côte sur grand écran, empilées sur mobile.

**Question :** que se passe-t-il quand la fenêtre devient plus étroite que 768 px ? Quelle classe provoque ce comportement ?

Documentation : [Grid](https://getbootstrap.com/docs/5.3/layout/grid/) · [Card](https://getbootstrap.com/docs/5.3/components/card/) · [List group](https://getbootstrap.com/docs/5.3/components/list-group/)

## Étape 4 – Tableau (15 min)

**À faire :**

1. Ajoutez au `<table>` les classes `table table-striped table-hover`.
2. Entourez le tableau d'un `<div class="table-responsive">`.
3. Donnez à l'en-tête (`<thead>`) un fond sombre avec `table-dark`.
4. Signalez les lignes anormales : `table-danger` sur la ligne au statut « Alerte », `table-warning` sur les lignes « À surveiller ».

**Question :** à quoi sert `table-responsive` ? Comment le vérifiez-vous dans le navigateur ?

Documentation : [Tables](https://getbootstrap.com/docs/5.3/content/tables/)

## Étape 5 – Formulaire (15 min)

**À faire :**

1. Sur le `<div>` de la section *Nouvelle mesure* : transformez-le en card (`card`), avec un en-tête (`card-header` sur le `<h2>`) et le formulaire dans un `<div class="card-body">`.
2. Donnez au `<form>` la classe `row g-3`.
3. Pour chaque champ : classe `col-md-6` (ou `col-md-4`, à vous de choisir pour que la ligne soit équilibrée) sur le `<div>`, `form-label` sur le `<label>`, `form-control` sur l'`<input>` ou le `<textarea>`. Le commentaire et le bouton occupent toute la largeur (`col-12`).
4. Donnez au bouton les classes `btn btn-primary`.

> Le formulaire n'envoie rien (il n'y a pas de serveur) : c'est normal, seul l'aspect nous intéresse ici.

**Question :** pourquoi chaque `<label>` possède-t-il un attribut `for` qui correspond à l'`id` d'un champ ?

Documentation : [Forms – Layout](https://getbootstrap.com/docs/5.3/forms/layout/) · [Form control](https://getbootstrap.com/docs/5.3/forms/form-control/)

## Étape 6 – Utilities (10 min)

Les *utilities* sont de petites classes qui évitent d'écrire du CSS. À faire :

1. **Constantes vitales** : sur chaque `<li>` de la card « Dernières constantes », ajoutez `d-flex justify-content-between align-items-center` (libellé à gauche, valeur à droite). Remplacez ensuite les `<strong>` des 4 mesures par des badges : `<span class="badge text-bg-warning">` pour la tension, `text-bg-success` pour les autres.
2. **Tableau** : dans la colonne *Statut*, transformez le texte en badge (`text-bg-success` pour Normal, `text-bg-warning` pour À surveiller, `text-bg-danger` pour Alerte).
3. **Cards** : ajoutez une ombre légère avec `shadow-sm`.
4. **Page** : ajoutez des espacements (`py-4` sur `<main>`, `mb-4` entre les blocs), `lead text-body-secondary` sur le paragraphe d'introduction, et centrez le pied de page (`text-center text-body-secondary py-3` sur `<footer>`).

Documentation : [Badges](https://getbootstrap.com/docs/5.3/components/badge/) · [Spacing](https://getbootstrap.com/docs/5.3/utilities/spacing/) · [Shadows](https://getbootstrap.com/docs/5.3/utilities/shadows/) · [Flex](https://getbootstrap.com/docs/5.3/utilities/flex/)

## Étape 7 – Bilan et rendu (10 min)

1. Testez votre page à **3 largeurs** (mobile ~375 px, tablette ~768 px, bureau) avec le mode appareil du navigateur. Rien ne doit déborder horizontalement, sauf le tableau qui peut défiler à l'intérieur de son bloc.
2. Répondez à la dernière question de `reponses.md` (avantages et limite de Bootstrap).
3. **Rendu sur GitHub** (au choix de l'enseignant) :
   - *sans Git* : créez un dépôt personnel `tp-bootstrap-nom`, puis **Add file → Upload files** pour déposer `index.html` et `reponses.md` ;
   - *avec Git* : `git add .`, `git commit -m "TP Bootstrap"`, `git push`.

   Communiquez ensuite le lien de votre dépôt.

---

## Bonus (pour les plus rapides)

### Bonus A – Une seconde page

Créez `notes.html`, la page des **notes de suivi** du patient :

- la même navbar que `index.html`, avec un lien **Notes** ajouté (et un lien de retour vers `index.html`) ;
- un titre `<h1>`, un paragraphe d'introduction, puis 3 notes datées dans un `list-group` (classe `list-group-item` pour chaque note) ;
- pensez à utiliser `active` et `aria-current="page"` sur le lien de la page courante.

### Bonus B – Un bandeau d'accueil (« hero »)

Remplacez le `<h1>` et le paragraphe d'introduction de `index.html` par un bandeau d'accueil inspiré de l'exemple [Jumbotron](https://getbootstrap.com/docs/5.3/examples/jumbotron/) : fond clair (`bg-body-tertiary`), coins arrondis (`rounded-3`), grand titre (`display-5 fw-bold`) et un bouton d'appel à l'action (`btn btn-primary btn-lg`) qui renvoie vers le formulaire.

### Expérimenter

Changez les couleurs des badges, testez le thème sombre avec `data-bs-theme="dark"` sur `<html>`, ajoutez une image… rien n'est trop fou.

---

## Évaluation

| Critère | Points |
|---|---|
| Bootstrap chargé sans erreur (CSS + JS, `integrity` conservé) | 3 |
| Navbar responsive qui fonctionne | 3 |
| Grille et cards (2 colonnes → 1 colonne sur mobile) | 4 |
| Tableau (classes, `table-responsive`, lignes colorées) | 3 |
| Formulaire (grille, `form-control`, labels liés aux champs) | 3 |
| Utilities et cohérence visuelle | 2 |
| Réponses aux questions (`reponses.md`) | 2 |
| **Total** | **20** |

Les bonus A et B rapportent jusqu'à 2 points supplémentaires, dans la limite de 20.
