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

## Sponsors — modèle 2026 (4 packs)

Source : *Dossier de sponsoring 2026* (équipe organisatrice). Chaque pack a un **bandeau couleur figé**. Bandeaux toujours en **majuscules blanches sur la couleur du tier**.

| Pack | Couleur | Hex | Quota | Tarif | Stand |
|------|---------|-----|-------|-------|-------|
| **Platinum** | Malachite (= identité DevFest) | `#109E6E` | 4 max | 8 000 € HT | 12 m² |
| **Gold** | Orange | `#FFAB40` | 20 max | 4 000 € HT | 6 m² |
| **Discovery** | Violet | `#7E60C9` | 8 max | 1 200 € HT | 2 m² (corner) |
| **Soutien** | Gris | `#CCCCCC` | sans limite | 500 € HT | aucun (focus visibilité) |

> **Discovery** est explicitement réservé aux **nouveaux sponsors, startups, TPE et associations**. Ce n'est pas un « pack discount » : c'est un pack d'entrée pour des structures qui n'auraient pas accès aux autres tarifs. À communiquer comme tel dans la copy.

> **Platinum réutilise le hex Malachite `#109E6E`** — la même couleur que le mot *DevFest* du wordmark. C'est intentionnel : le pack Platinum mérite la couleur d'ancrage de la marque. Cela ne contredit pas la règle « Malachite = wordmark DevFest » : le bandeau est un signal contextuel, pas le wordmark.

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
| White | Malachite / Tier-Platinum `#109E6E` | 3.6:1 ⚠️ (texte ≥ 18 px Bold ou ≥ 24 px) |
| White | Terracotta `#EC6839` | 3.4:1 ⚠️ (texte ≥ 18 px Bold ou ≥ 24 px) |
| White | Bismarck `#B94420` | 5.6:1 ✅ |
| White | Tier-Gold `#FFAB40` | 2.0:1 ❌ (utiliser **ink** sur ce fond, pas blanc) |
| White | Tier-Discovery `#7E60C9` | 5.4:1 ✅ |
| White | Tier-Soutien `#CCCCCC` | 1.6:1 ❌ (utiliser **ink** sur ce fond) |
| Ink   | Tier-Gold `#FFAB40` | 8.6:1 ✅ |
| Ink   | Tier-Soutien `#CCCCCC` | 11.0:1 ✅ |

> ⚠️ Pour les tiers **Gold** et **Soutien**, le label du bandeau doit être en **ink** (`#1D1D1B`) plutôt qu'en blanc, sinon le contraste ne passe pas WCAG AA. Pour Platinum et Discovery, blanc reste correct.
