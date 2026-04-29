# Couleurs — DevFest Toulouse

> **Valeurs hexa de référence** : voir [`../DESIGN.md`](../DESIGN.md) (front matter YAML).
> Ce document explique **quand et pourquoi** utiliser chaque couleur, pas leur valeur exacte.

## Trois familles, trois rôles

```
Identité chaude (Toulouse)        Identité fraîche (DevFest)        Action (fonctionnel)
─────────────────────────         ─────────────────────────         ─────────────────────
Bismarck       #B94420            Malachite       #109E6E            Bleu CTA       #507BBD
Terre cuite    #EC6839            Émeraude        #41B38E
Incarnadin     #F4A598            Menthe          #8BCBB7
                                  Eau             #C0E1D7
```

### Identité chaude (Toulouse)

Chaleur de la brique. À utiliser pour tout ce qui dit « Toulouse » : titre du wordmark, accents H1 hero, hover des CTA, illustrations chaudes.

- **Terre cuite `#EC6839`** — *la* couleur identitaire chaude. Wordmark « Toulouse », accents.
- **Bismarck `#B94420`** — version sombre, pour les liens auteur d'article et les accents qui doivent passer test contraste WCAG AA.
- **Incarnadin `#F4A598`** — version claire, fonds doux et accents.

### Identité fraîche (DevFest)

Calme, anchor de page, sponsor Platinum. Wordmark « DevFest », footer, accents verts.

- **Malachite `#109E6E`** — *la* couleur identitaire fraîche. Wordmark « DevFest », fond du footer.
- **Émeraude `#41B38E`** — bandeau Platinum, accents.
- **Menthe `#8BCBB7`** / **Eau `#C0E1D7`** — fonds verts clairs.

### Action (fonctionnel, pas identitaire)

Le **bleu** porte l'action. Il n'est *pas* une couleur d'identité — c'est une couleur de bouton. Cette distinction protège la lisibilité des CTA contre le bruit de la palette identitaire.

- **Bleu `#507BBD`** — fond des CTA principaux, bordure des CTA secondaires.
- **Bleu 2 `#63C6F2`** / **Bleu 3 `#C4E6F1`** — accents et fonds clairs (rares).

## Sponsors

Chaque tier de sponsor a son bandeau couleur, intégralement réservé :

| Tier | Couleur | Hex |
|------|---------|-----|
| Platinum | Émeraude | `#41B38E` |
| Gold | Jaune | `#FFD428` |
| Silver / autre | Rose | `#EE7CAD` |

Ne jamais dévier de cette correspondance ; elle est immédiatement lisible par les sponsors récurrents.

## Sémantique

| Usage | Couleur | Hex |
|-------|---------|-----|
| Texte principal | Noir | `#1D1D1B` |
| Texte navigation | Gris | `#777776` |
| Texte secondaire (date, mentions) | Gris clair | `#8E8E8D` |
| Lien dans le corps | Bismarck | `#B94420` |
| Lien sur fond sombre (footer) | Blanc cassé | `#FDF0EB` |
| Erreur / alerte | Rouge | `#E84336` |
| Fond de page | Blanc | `#FFFFFF` |

## Règles d'association

✅ **À faire**
- « DevFest » en malachite, « Toulouse » en terre cuite — toujours.
- CTA en bleu, fond blanc, texte blanc sur le bleu.
- Footer malachite, liens en blanc cassé `#FDF0EB`.
- Sur fond Émeraude (Platinum) : texte blanc.

❌ **À ne jamais faire**
- Inverser malachite et terre cuite sur le wordmark.
- Utiliser le bleu CTA comme couleur d'identité (titre, fond de section).
- Mettre du texte sombre sur Bismarck (`#B94420`) sans vérifier le contraste — souvent insuffisant.
- Introduire une nouvelle couleur sans l'ajouter d'abord dans `DESIGN.md`.

## Accessibilité

Toutes les associations texte/fond utilisées en production doivent atteindre **WCAG 2.1 AA** (contraste ≥ 4.5:1 pour texte courant, ≥ 3:1 pour grand texte ≥ 24 px). En cas de doute, vérifier avec un outil type [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) ou la commande `npx design-md lint`.

Les paires sûres :

| Texte | Fond | Ratio |
|-------|------|-------|
| Ink `#1D1D1B` | White `#FFFFFF` | 17.4:1 ✅ |
| White | Blue CTA `#507BBD` | 4.7:1 ✅ |
| White | Malachite `#109E6E` | 3.6:1 ⚠️ (texte ≥ 18 px Bold ou ≥ 24 px) |
| White | Terracotta `#EC6839` | 3.4:1 ⚠️ (texte ≥ 18 px Bold ou ≥ 24 px) |
| White | Bismarck `#B94420` | 5.6:1 ✅ |
