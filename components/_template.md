---
name: NomDuComposant            # PascalCase, identique au code (relié au nom Figma dans « Correspondance avec Figma »)
description: Une phrase - à quoi sert le composant.
status: beta                    # stable | beta | deprecated
category: basics
code: src/components/ui/nom-du-composant.tsx
figma:
  file: CLE_DU_FICHIER_FIGMA
  node: "0:0"
variants:                       # axes de variation et leurs valeurs, dans le même ordre que les props
  size: [sm, default, lg]
props:                          # type : enum | boolean | string | number | node
  - { name: size, type: enum, values: [sm, default, lg], default: default }
  - { name: disabled, type: boolean, default: false }
states: [default, hover, focus, disabled]   # default | hover | focus | active | disabled | loading | error | readOnly | checked | indeterminate
tokens:                         # tous les tokens cités dans le corps, par leur nom
  - color.surface.main
related: []
updated: AAAA-MM-JJ
---

# NomDuComposant

Une phrase : à quoi sert le composant.

## Usage

**Utiliser quand :**

- …

**Ne pas utiliser quand :**

- … → alternative : …

Chaque « ne pas utiliser » donne son alternative. Une règle explicite répond à cinq questions : condition, action, limite, alternative, raison.

## Variantes et états

| Variante | Rôle | Règle |
|---|---|---|
| … | … | … |

| État | Comportement |
|---|---|
| Repos | … |
| Désactivé | … |

Décrire le comportement de chaque état, pas seulement son apparence.

## Tokens utilisés

| Partie | État | Tokens |
|---|---|---|
| `container` | repos | fond `color.surface.main` |

Tokens cités par leur nom, jamais par leur valeur.

## Accessibilité

- Élément natif : …
- Clavier : …
- Focus : …
- Contraste : …

## Exemples

```tsx
// un exemple par variante ou par cas d'usage
```

## Do et Don't

- **Do :** …
- **Don't :** …

---

Les sections suivantes complètent le template de la formation.

## Anatomie

| Partie | Rôle |
|---|---|
| `container` | … |

## Correspondance avec Figma

| Dans Figma | Dans le code |
|---|---|
| … | … |

## Limites connues

- …

## Implémentation de référence

[`src/components/ui/nom-du-composant.tsx`](../../src/components/ui/nom-du-composant.tsx)
