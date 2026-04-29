# Typographie — DevFest Toulouse

> **Échelle complète et tokens** : voir [`../DESIGN.md`](../DESIGN.md) section `typography`.

## Police principale — Google Sans

**Google Sans** (anciennement Product Sans, créée par Google) est la **seule** police utilisée sur le web et le digital DevFest Toulouse. Elle porte le logo DevFest officiel et chaque écran du site.

- Disponible sur [Google Fonts](https://fonts.google.com/specimen/Google+Sans)
- Licence : **SIL Open Font License** (depuis novembre 2025)
- Usage commercial et open-source autorisé

### Variantes utilisées

| Variante | Usage |
|----------|-------|
| **Bold (700)** | Titres, boutons, chiffres clés, noms |
| **Medium (500)** | Emphase intermédiaire dans un paragraphe, labels secondaires, boutons en zones denses |
| **Regular (400)** | Corps de texte, descriptions, navigation, labels |
| **Italic (400/500/700)** | **Uniquement** baselines de sponsors Platinum |

> ⚠️ Italic n'est *pas* utilisé pour de l'emphase dans le corps de texte. Pour appuyer un mot, on utilise **Bold** ou **Medium** (Medium si Bold est trop fort dans le contexte).

### Chargement web — recommandation

**Par défaut : CDN Google Fonts.** Plus simple, mises à jour automatiques, cache CDN partagé entre sites.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Google+Sans:ital,wght@0,400;0,500;0,700;1,400;1,500;1,700&display=swap" rel="stylesheet">
```

```css
font-family: 'Google Sans', system-ui, sans-serif;
```

### Chargement web — bascule self-hosted

Si la production a une contrainte (CSP, RGPD strict, fonctionnement offline, perte d'accès au CDN), basculer en self-hosted :

1. Les fichiers `.ttf` sont déjà dans [`../assets/fonts/`](../assets/fonts/) :
   - `GoogleSans-Regular.ttf`, `GoogleSans-Italic.ttf`
   - `GoogleSans-Medium.ttf`, `GoogleSans-MediumItalic.ttf`
   - `GoogleSans-Bold.ttf`, `GoogleSans-BoldItalic.ttf`
2. Référencer [`../tokens/colors_and_type.css`](../tokens/colors_and_type.css) qui contient déjà les `@font-face` correspondants.
3. Retirer le `<link>` Google Fonts CDN.

> 💡 Une optimisation possible : convertir les `.ttf` en `.woff2` (~30 % plus léger) et mettre à jour les `@font-face` correspondants. Tâche à planifier si la perf devient un sujet.

## Police secondaire — CCSignLanguage

Police **manuscrite** utilisée en seconde lecture pour évoquer le partage et la convivialité.

| Usage | Contexte |
|-------|----------|
| Accroches, citations | Visuels print, réseaux sociaux |

> ❌ **CCSignLanguage n'est jamais utilisée sur le web.** Son usage est strictement réservé aux supports de communication (visuels Twitter/LinkedIn, affiches, kakémonos).

## Échelle typographique

Voir le tableau complet dans [`../DESIGN.md`](../DESIGN.md). Synthèse des usages :

| Niveau | Token | Quand l'utiliser |
|--------|-------|------------------|
| Hero | `display` (112 px) | Titre du hero d'accueil — « DevFest Toulouse » |
| Section | `heading-1` (64 px) | Titres de grande section |
| Sous-section | `heading-2` (48 px) | Sous-sections |
| H3 | `heading-3` (40 px) | Noms sponsors Platinum, valeurs statistiques |
| Hero description | `description` (32 px) | Texte d'introduction du hero |
| Carte (titre) | `card-title-l/m/s` | Selon taille de carte |
| Body | `body` (16 px) | Texte courant, navigation, footer |
| Caption | `caption` (12 px) | Auteurs, métadonnées |
| Petit | `small` (10 px) | Dates, « by », mentions |

## Règles

✅ **À faire**
- Une seule famille (Google Sans) sur le web. Toujours.
- **Bold** pour l'emphase, jamais Italic.
- Line-height généreux : 100 % pour les hero (impact), 120-160 % pour le confort de lecture.
- `letter-spacing` 0.4 px pour la navigation et les CTA Small (lisibilité à petite taille).

❌ **À ne jamais faire**
- Utiliser une autre police sans-serif (Roboto, Inter, Helvetica) « parce qu'elle ressemble ».
- Mettre du Italic dans un paragraphe.
- Utiliser CCSignLanguage en HTML/CSS.
- Descendre sous 12 px pour du texte fonctionnel (les `small` 10 px sont réservés aux mentions très courtes).
