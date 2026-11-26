# Notes pour l'enseignant – TP Bootstrap « Fiche patient »

> À ne pas distribuer aux étudiants (voir « Publier sur GitHub » plus bas).

## Contenu du dépôt

```
tp-bootstrap-fiche-patient/
├── README.md                  énoncé destiné aux étudiants
├── ENSEIGNANT.md              ce fichier
├── starter/
│   ├── index.html             fichier de départ (contenu saisi, sans Bootstrap)
│   └── reponses.md            questions de compréhension à compléter
└── corrige/
    ├── index.html             corrigé des étapes 1 à 7
    └── bonus/
        ├── index.html         corrigé avec bandeau « hero » + lien vers les notes
        └── notes.html         corrigé de la seconde page
```

## Publier sur GitHub

Le plus simple pour ne pas exposer le corrigé aux étudiants :

1. **Dépôt privé « enseignant »** : tout le contenu, y compris `corrige/` et ce fichier.
2. **Dépôt public (ou modèle) « étudiants »** : uniquement `README.md` et `starter/`. Dans les paramètres du dépôt, cochez *Template repository* : chaque étudiant clique sur **Use this template** et obtient son propre dépôt, sans manipulation de Git.

Alternatives : GitHub Classroom (distribution et collecte automatisées des rendus), ou un dépôt unique avec un lien de téléchargement ZIP du seul dossier `starter/`.

Option pour visualiser les rendus : activer **GitHub Pages** (Settings → Pages) sur le dépôt d'un étudiant publie sa page à une adresse web, sans outil supplémentaire.

## Déroulé minuté

| Min | Étape | Point de vigilance |
|---|---|---|
| 0–10 | 1. Mise en place | Les étudiants copient souvent le `<link>` mais oublient le `<script>` (la navbar ne se replie alors pas). |
| 10–20 | 2. Navbar | Comparer `navbar-dark` (ancienne syntaxe, présente dans beaucoup de tutoriels) et `data-bs-theme="dark"` (5.3). |
| 20–40 | 3. Grille et cards | Étape la plus conceptuelle : insister sur la séquence `row` → `col-*` → contenu. |
| 40–55 | 4. Tableau | `table-responsive` se vérifie en réduisant la fenêtre à ~375 px. |
| 55–70 | 5. Formulaire | Faire cliquer sur un libellé : le champ prend le focus grâce à `for`/`id`. |
| 70–80 | 6. Utilities | Ctrl + D pour appliquer une classe à plusieurs `<li>` d'un coup. |
| 80–90 | 7. Bilan et rendu | Prévoir un temps réel pour le dépôt GitHub si c'est la première fois. |

## Erreurs fréquentes

- **`col-*` sans `row`** : les colonnes ne se placent pas côte à côte.
- **`container` oublié** : le contenu occupe toute la largeur de l'écran.
- **`integrity` modifié ou tronqué à la copie** : le navigateur bloque la ressource et la page apparaît sans mise en forme (erreur visible dans la console).
- **Classes appliquées au mauvais niveau** : par exemple `table-danger` sur le `<td>` au lieu du `<tr>` (cela fonctionne, mais colore une seule cellule).
- **`<label>` sans `for`/`id`** : le champ n'est plus relié à son libellé.

## Points techniques à connaître

- **Réseau obligatoire** : Bootstrap est chargé depuis un CDN (jsDelivr). Si la salle de TP n'a pas d'accès Internet fiable, téléchargez Bootstrap (page *Download* de la documentation) et distribuez les fichiers avec `starter/`, en adaptant les chemins du `<link>` et du `<script>`.
- **Version** : le corrigé utilise Bootstrap **5.3.9**, avec les liens et les empreintes `integrity` copiés depuis la page *Get started* de la documentation officielle. Si vous changez de version, recopiez les deux balises depuis cette page : l'empreinte est propre à chaque fichier et à chaque version.
- **Statuts et seuils** : ils sont purement illustratifs. Si vous les présentez comme des seuils cliniques, indiquez les sources que vous retenez.

## Barème

Le barème sur 20 points figure en bas du `README.md` (visible des étudiants). Les bonus A et B rapportent jusqu'à 2 points, plafonnés à 20.

## Variantes possibles

- **Plus court (1h)** : supprimer l'étape 6 (utilities) et fournir la navbar toute faite.
- **Plus long (2h)** : ajouter les bonus A et B au parcours obligatoire.
- **Pour aller plus loin** : lier le formulaire à un script JavaScript qui ajoute une ligne au tableau (nouveau TP).
