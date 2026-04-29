# Using this design system with Claude Design

Ce dépôt est conçu pour servir de **contexte de marque** lors de la génération de maquettes par Claude Design (ou tout autre agent IA conforme au format [Stitch DESIGN.md](https://github.com/google-labs-code/design.md)).

## Le fichier qui compte

Un seul fichier suffit pour informer un agent : [`../DESIGN.md`](../DESIGN.md).

Il contient :

- **YAML front matter** — palette, typographie, espacement, radius, composants — au format normatif Stitch.
- **8 sections markdown** — rationale humain (Overview, Colors, Typography, Layout, Elevation, Shapes, Components, Do's and Don'ts).

## Workflows

### Générer une nouvelle maquette avec Claude Design

1. Pointer Claude Design sur ce dépôt (par URL ou en collant le contenu de `DESIGN.md` dans le prompt).
2. Donner aussi 1 à 3 SVG de [`../examples/`](../examples/) si la page à générer ressemble à une page existante (article, profil, formulaire).
3. Demander : « Génère une maquette de page FAQ, en respectant le DESIGN.md de DevFest Toulouse. »
4. Claude Design utilisera les tokens nommés (`{colors.primary}`, `{rounded.3xl}`, etc.) au lieu d'inventer des hexa et des radius arbitraires.

### Générer du code à partir d'une maquette

1. Donner à Claude Code (ou autre code agent) la maquette **+** le `DESIGN.md`.
2. L'agent peut convertir une référence `{colors.primary}` en variable CSS / token Tailwind / token DTCG selon le projet cible.
3. Quand [`../tokens/`](../tokens/) sera peuplé, fournir aussi le format adapté à la stack (Tailwind config, CSS vars).

### Itérer une maquette générée

Quand le résultat dérive (couleur off-brand, radius incorrect) :

1. Identifier précisément le token attendu : « le bouton primaire devrait être `{colors.primary}` (`#507BBD`), pas `#3B82F6` ».
2. Pointer la règle violée dans le DESIGN.md ou dans `brand/` (ex. *« voir Do's and Don'ts : la primary est bleue, pas malachite »*).
3. Re-prompter avec la correction explicite.

## Pourquoi DESIGN.md fonctionne mieux que des screenshots

Un agent qui voit un screenshot doit deviner les valeurs (« on dirait du `#EC6839` ») et les rôles (« on dirait que c'est la couleur de fond du bouton »). Un agent qui voit `DESIGN.md` :

- a les hexa **exacts**,
- connaît leurs **rôles sémantiques** (`primary`, `secondary`, `error`),
- sait **pourquoi** (Do's and Don'ts),
- peut **valider** sa sortie via `npx design-md lint`.

## Limites connues

- Le format `DESIGN.md` est en `alpha` — la spec peut bouger. Suivre les releases sur [google-labs-code/design.md](https://github.com/google-labs-code/design.md/releases).
- Les **illustrations** ne sont pas exprimables en YAML — leur usage relève de [`../brand/illustrations.md`](../brand/illustrations.md). Pour qu'un agent les utilise correctement, fournir aussi cette page (ou un résumé) dans le contexte.
- Les **interactions** (animations, transitions) ne sont pas couvertes par le format alpha. À documenter à part dans [`../components/`](../components/) si besoin.

## Aller plus loin

- [Spec officielle](https://github.com/google-labs-code/design.md)
- [Annonce de l'open-sourcing du format](https://blog.google/innovation-and-ai/models-and-research/google-labs/stitch-design-md/)
- [Stitch — Design with AI](https://stitch.withgoogle.com/)
