# DevFest Toulouse — Design System

Référentiel unique de l'identité visuelle du **DevFest Toulouse**, organisé par le GDG Toulouse.

Ce dépôt sert trois publics et trois usages :

| Public | Ce qu'ils trouvent | Où regarder |
|--------|--------------------|-------------|
| 👤 **Humains** (orgas, partenaires, sponsors, créateurs de contenu) | Charte de marque, règles d'usage du logo, palette, ton et voix, illustrations | [`brand/`](brand/) |
| 🤖 **Agents IA** (Claude Design, Stitch, autres outils de génération de maquettes) | Tokens machine-readable + rationale, au format [Google Stitch DESIGN.md](https://github.com/google-labs-code/design.md) | [`DESIGN.md`](DESIGN.md) |
| 💻 **Développeurs** d'applications DevFest Toulouse | Tokens exportables, spécifications de composants, assets prêts à intégrer | [`tokens/`](tokens/), [`components/`](components/), [`assets/`](assets/) |

---

## Pourquoi ce dépôt

Jusqu'en 2025, l'identité visuelle du DevFest Toulouse vivait dispersée : PDF de charte 2024, fichier Figma, exports SVG dans le repo du site, conventions implicites. Cette dispersion a deux problèmes :

1. **Pour les humains** : pas de référence canonique pour répondre à « est-ce que je peux utiliser cette couleur sur ce fond ? »
2. **Pour les agents IA** : un agent qui génère une maquette ne sait pas où chercher la palette ni dans quel format la consommer.

Ce dépôt résout les deux : la **prose** est pour les humains, le **`DESIGN.md`** est pour les machines, les deux pointent vers les mêmes assets.

## État

🚧 **Alpha.** La marque est stable depuis 2024, le `DESIGN.md` suit la spec `version: alpha` de Stitch et évoluera avec elle.

## Structure

```
.
├── DESIGN.md             ← Spec machine-readable (format Stitch)
├── brand/                ← Charte de marque (humain, FR)
├── tokens/               ← Tokens exportables (DTCG, Tailwind, CSS vars)
├── components/           ← Spécifications composants (HTML/CSS de référence)
├── assets/               ← Logo, illustrations, polices, charte PDF
├── examples/             ← Maquettes de référence (site DevFest 2026)
└── docs/                 ← Guides d'usage (intégration, Claude Design, etc.)
```

## Sources

- Charte graphique 2024 (PDF) : [`assets/charte-graphique-2024.pdf`](assets/charte-graphique-2024.pdf)
- Maquettes Figma 2025 : [DevFestToulouse-2025](https://www.figma.com/design/5dw9ggMfrdFrB9qEKYvHH6/DevFestToulouse-2025?node-id=22-499)
- Site DevFest 2026 (consommateur de référence) : `../Site-Devfest-Toulouse-2026/`

## Licence

Voir [LICENSE](LICENSE).
