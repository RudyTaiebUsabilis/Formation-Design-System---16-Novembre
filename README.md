# Design System IA Ready

Source unique de vérité du design system : **tokens**, **composants**, **documentation** et **règles**, lisibles par les humains et exploitables par les IA (Claude Code, Codex, Cursor, Lovable via MCP).

> Une bibliothèque décrit ce qui existe. Ce dépôt explique aussi **pourquoi**, **quand** et **comment** l'utiliser.

## Structure

```
design-system-ia/
├── README.md               ← vous êtes ici : vue d'ensemble
├── AGENTS.md               ← règles pour les agents IA (Codex, Cursor, Lovable…)
├── CLAUDE.md               ← point d'entrée Claude Code (renvoie vers AGENTS.md)
├── GOVERNANCE.md           ← rôles, validation, versioning
├── CONTRIBUTING.md         ← comment proposer une modification
├── CHANGELOG.md            ← historique des versions
├── .mcp.json               ← connexion MCP (Figma)
├── tokens/                 ← Design Tokens au format W3C (DTCG)
│   ├── primitives.tokens.json
│   ├── semantic.light.tokens.json
│   └── semantic.dark.tokens.json
├── docs/                   ← documentation Markdown
│   ├── foundations/        ← couleurs, typographie, espacements
│   ├── components/         ← une fiche par composant (_template.md + button.md)
│   ├── patterns/           ← assemblages récurrents (formulaire, confirmation…)
│   └── rules/              ← nommage, rédaction, accessibilité
├── src/                    ← implémentation de référence (React + Tailwind)
│   ├── components/ui/
│   ├── lib/
│   └── styles/tokens.css   ← tokens traduits en variables CSS
├── prompts/                ← prompts réutilisables et testés
├── resources/              ← liens Figma, assets
└── .github/                ← templates de PR et d'issues, CODEOWNERS
```

## Qui lit quoi ?

| Lecteur | Point d'entrée | Ce qu'il y cherche |
|---|---|---|
| **Designer** | `docs/`, `resources/figma.md` | Règles d'usage, correspondance Figma ↔ code |
| **Développeur** | `src/`, `tokens/`, `docs/components/` | Props, variantes, tokens, exemples |
| **Agent IA** | `AGENTS.md` puis `docs/` et `tokens/` | Contraintes explicites, noms stables, exemples représentatifs |
| **Équipe DS** | `GOVERNANCE.md`, `CHANGELOG.md` | Processus de validation, versions |

## Principes

- **Source unique de vérité** : une décision n'existe qu'à un seul endroit. Figma, le code et la doc s'y réfèrent.
- **Tokens d'abord** : aucune valeur en dur dans un composant. Primitives → sémantiques → composants.
- **Documenter pour un lecteur sans contexte** : chaque règle donne sa condition, son action, sa limite, son alternative et sa raison.
- **Tout passe par une Pull Request** : rien n'arrive sur `main` sans relecture (voir `GOVERNANCE.md`).

## État de départ

| Élément | État |
|---|---|
| Tokens couleurs (primitives + sémantiques Light / Dark) | ✅ |
| Tokens espacements, tailles, rayons (utilisés par Button) | ✅ partiel |
| Typographie (tokens) | ⬜ à faire |
| Composant `Button` (doc + code) | ✅ beta |
| Composants `ButtonIcon`, `Input` | ⬜ à documenter |
| Patterns | ⬜ à faire |

## Démarrer

```bash
git clone <url-du-depot>
```

Puis lisez `AGENTS.md` (même si vous êtes humain : c'est le résumé des règles).
