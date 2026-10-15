# Organisation des styles

Les pages HTML chargent désormais des feuilles CSS externes, dans cet ordre :

1. `commun.css` : styles partagés par toutes les pages (couleurs, typographie, en-tête, navigation, logos et pied de page).
2. `contenu.css` : styles partagés par les pages intérieures, sans les deux pages d'accueil.
3. `pages/<nom>.css` : particularités de la page et adaptations aux petits écrans. Les axes 1 à 3 et les WP 2 à 4 partagent `pages/contenu-standard.css`. Les pages Accessibilité et Mentions légales partagent `pages/informations.css`.

Les fichiers chargés plus tard complètent ou remplacent les règles précédentes. Conserver cet ordre dans les balises `<link>`.

## Modifier le site

- Pour changer une couleur globale, modifier les variables de `:root` dans `commun.css`.
- Pour modifier la taille du logo principal ou des partenaires, modifier `.logo img` ou les règles `.header-partners` dans `commun.css`. Les tailles sur petit écran se trouvent aussi dans les blocs `@media` de ce fichier.
- Pour modifier l'apparence des contenus intérieurs, commencer par `contenu.css`, puis vérifier les éventuelles variantes dans le fichier de la page.
- Pour une modification propre à une page, utiliser son fichier dans `pages/`. Si elle utilise `contenu-standard.css`, une modification de ce fichier concerne toutes les pages qui le chargent ; créer une feuille supplémentaire pour une exception individuelle.

## Remplacer les images des logos

Les images restent dans `assets/`. Remplacer une image en conservant son nom actualise toutes les pages qui l'utilisent : `header-logo.png` pour le logo principal en haut, `footer-logo.png` pour celui du pied de page, `unys-logo.png` et `france2030-insight-logo.png` pour les deux partenaires en haut à droite. UNYS et France 2030 ne sont plus présents dans le pied de page. Les autres logos existants (Université de Lorraine et CNRS sur le plan du site) sont conservés.

Le CSS contrôle l'apparence des logos, pas leur attribut HTML `src`, leur texte alternatif ou leur lien. L'en-tête et le pied de page HTML restent présents dans chaque page.

## Ajouter une page

Copier les balises `<link rel="stylesheet">` d'une page similaire. Charger `commun.css`, puis `contenu.css` pour une page intérieure, puis la feuille adaptée dans `pages/`. Aucun outil de compilation ni serveur particulier n'est nécessaire.

Les chemins d'images dans un fichier CSS sont relatifs à ce fichier : `../hero-bg.png` depuis `assets/css/` et `../../hero-bg.png` depuis `assets/css/pages/`.
