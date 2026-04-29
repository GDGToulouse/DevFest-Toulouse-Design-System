# Illustrations — DevFest Toulouse

## Style

Les illustrations DevFest Toulouse suivent un style **croquis / esquisse** (hand-drawn). Trait libre, monochrome, pas de remplissage opaque, pas d'ombre. L'effet recherché : un **carnet de notes de dev toulousain**.

## Palette d'illustration

Chaque illustration est déclinée dans **3 couleurs identitaires** :

| Couleur | Hex | Quand l'utiliser |
|---------|-----|------------------|
| **Bismarck** | `#B94420` | Sur fond clair, version la plus contrastée |
| **Terre cuite** | `#EC6839` | Sur fond clair, version chaude/identitaire |
| **Malachite** | `#109E6E` | Sur fond clair, version verte/identitaire |

Les fichiers PNG correspondants sont rangés dans :
- [`../assets/illustrations/Bismarck/`](../assets/illustrations/)
- [`../assets/illustrations/TerreCuite/`](../assets/illustrations/)
- [`../assets/illustrations/Malachite/`](../assets/illustrations/)

> ⚠️ **Aucune autre couleur n'est autorisée.** Pas de blanc, pas de bleu, pas de gradient. Si une nouvelle couleur d'illustration est nécessaire, elle doit être ajoutée à `DESIGN.md` *et* faire l'objet d'un export complet du catalogue.

## Catalogue (30 illustrations)

| Catégorie | Illustrations |
|-----------|---------------|
| **Monuments toulousains** | La Grave, Pont Neuf |
| **Symboles toulousains** | Croix occitane, Violette, Étoile |
| **Personnages** | Geek, Geeke |
| **Restauration** | Burger, Croissant, Café, Cocktail, Boisson fraîche, Sandwich, Miam |
| **Tech / Web** | Site Web, Site Web 2, DevFest |
| **Décoration** | Flèche (×3), Soulignement (×3), Accolade gauche/droite, Entouré (×3), Expression, Exclamation, Point d'exclamation |
| **Événement** | Communauté, Sponsors, Micro, Vestiaire, Toilette |
| **Autres** | Tracteur, Monde Agri, Plane |

Total : **30 illustrations × 3 couleurs = 90 fichiers PNG.**

## Illustrations clés

Deux illustrations portent une charge identitaire forte et sont systématiquement réutilisées :

| Illustration | Emplacement type | Fichier |
|--------------|------------------|---------|
| **La Grave** | Section statistiques (en bas à gauche d'un encart blanc) | `LaGraveIlluDevFest.png` |
| **Croix occitane** | Section sponsors (en haut à droite, légèrement pivotée ~22°) | `CroixOccitaneIlluDevFest.png` |

## Usages

### Sur le site web

- En **filigrane** dans une section pour la signer (pas trop dense, max 2 illustrations par section).
- En **icône décorative** à côté d'un titre fort.
- En **fond** d'une carte / encart, à 10-30 % d'opacité.

### Sur les réseaux sociaux et le print

- En **élément central** d'un visuel d'annonce.
- Avec la police secondaire **CCSignLanguage** pour renforcer le côté carnet.

## Règles

✅ **À faire**
- Toujours utiliser un fichier officiel (pas de redessin à la volée).
- Respecter la couleur d'origine (Bismarck / Terre cuite / Malachite).
- Garder des marges autour : une illustration n'a pas besoin de toucher le bord.

❌ **À ne jamais faire**
- Recolorier une illustration en dehors des 3 couleurs autorisées.
- Étirer / déformer.
- Mettre une ombre portée ou un effet de filtre.
- Utiliser une illustration en very small format (< 32 px) — préférer Font Awesome pour les icônes fonctionnelles à cette taille.

## Format

- **Aujourd'hui** : PNG (transparent), résolution variable.
- **Évolution prévue** : conversion en SVG pour le poids et la scalabilité, à planifier comme tâche dédiée.

## Icônes fonctionnelles vs illustrations

Ne pas confondre :

| Type | Source | Usage |
|------|--------|-------|
| **Icônes fonctionnelles** | [Font Awesome](https://fontawesome.com/) Free 7 | UI, statistiques (calendrier, micro, mains qui se serrent, utilisateurs), réseaux sociaux |
| **Illustrations** | Catalogue ci-dessus | Décoration, identité, atmosphère |
