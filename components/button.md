---
name: Button
description: Déclenche une action immédiate sur la page ou dans un formulaire.
status: beta
category: basics
code: src/components/ui/button.tsx
figma:
  file: S5w6gdpuYhKzlqm0WW1Xu9
  node: "149:1855"
variants:
  variant: [default, destructive, outline, secondary, ghost, link]
  size: [sm, default, lg]
props:
  - { name: variant, type: enum, values: [default, destructive, outline, secondary, ghost, link], default: default }
  - { name: size, type: enum, values: [sm, default, lg], default: default }
  - { name: disabled, type: boolean, default: false }
  - { name: asChild, type: boolean, default: false }
  - { name: children, type: node }
states: [default, hover, focus, disabled]
tokens:
  - color.bg.primary-hover
  - color.bg.secondary
  - color.bg.secondary-hover
  - color.bg.accent
  - color.bg.destructive
  - color.bg.destructive-hover
  - color.text.default
  - color.text.on-primary
  - color.text.on-secondary
  - color.text.on-accent
  - color.text.on-destructive
  - color.text.link
  - color.icon.default
  - color.icon.on-primary
  - color.icon.on-secondary
  - color.icon.on-accent
  - color.icon.on-destructive
  - color.icon.link
  - color.strokes.default
  - color.strokes.focus
  - color.strokes.focus-ring
  - color.strokes.error-ring
  - spacing.1-5
  - spacing.2
  - spacing.3
  - spacing.4
  - spacing.6
  - size.8
  - size.9
  - size.10
  - radius.md
related: [ButtonIcon, Input]
updated: 2026-11-17
---

# Button

Déclenche une action immédiate sur la page ou dans un formulaire.

## Usage

**Utiliser quand :**

- **Action principale (`default`)** : l'utilisateur valide l'étape en cours (envoyer, enregistrer, continuer). Une seule par zone (formulaire, carte, modale), car l'œil doit trouver tout de suite l'action attendue.
- nouveauté
- **Action secondaire (`secondary` ou `outline`)** : l'action accompagne l'action principale (annuler, retour, brouillon). Placez-la à gauche de l'action principale, car l'ordre de lecture doit rester le même sur tous les écrans.
- **Action à faible poids (`ghost`)** : l'action est fréquente mais ne doit pas attirer l'œil (barre d'outils, en-tête de carte, filtre). Toujours avec un libellé visible, car sans fond rien n'indique sinon qu'on peut cliquer.
- **Action irréversible (`destructive`)** : l'action supprime ou révoque une donnée (supprimer un compte, retirer un membre). Toujours suivie d'une confirmation, car le style rouge prévient mais n'empêche pas l'erreur.
- **Libellé** : un verbe à l'infinitif, 1 à 3 mots (Ex : « Enregistrer », « Créer un projet »), car il doit annoncer le résultat du clic.

**Ne pas utiliser quand :**

- L'élément mène vers une autre page ou une URL → alternative : lien `<a>`, ou `Button variant="link" asChild` pour garder le style. Raison : un bouton n'ouvre pas de nouvel onglet et n'est pas annoncé comme un lien par les lecteurs d'écran.
- L'action n'a qu'une icône, sans libellé → alternative : `ButtonIcon`, avec un `aria-label` obligatoire. Raison : `Button` est dimensionné pour du texte, et une icône seule n'a pas de nom accessible.
- L'élément active ou désactive une option → alternative : `Switch` ou `Checkbox`. Raison : un bouton ne garde pas d'état visible après le clic.
- Plusieurs actions principales se trouvent dans la même zone → alternative : une seule en `default`, les autres en `secondary` ou `outline`. Raison : deux actions de même poids obligent l'utilisateur à choisir sans indice.
- Plus de 3 actions sont alignées côte à côte → alternative : garder les 2 plus fréquentes et regrouper le reste dans un `DropdownMenu`. Raison : au-delà, la ligne déborde sur mobile et la hiérarchie se perd.
- L'action est impossible tant qu'un champ n'est pas rempli → alternative : laisser le bouton actif et afficher l'erreur sur le champ (`Input` état error). Raison : un bouton `disabled` n'explique pas pourquoi il est bloqué et ne reçoit pas le focus clavier.

## Variantes et états

| Variante | Rôle | Règle |
|---|---|---|
| `default` | Action principale de la zone | Une seule par zone. Placée à droite dans un groupe de boutons. |
| `destructive` | Action irréversible (supprimer, révoquer) | Toujours suivie d'une confirmation. Jamais comme action par défaut d'un formulaire. |
| `outline` | Action secondaire sur fond chargé ou à côté d'un `default` | À gauche de l'action principale. Pas plus de 2 par groupe. |
| `secondary` | Action secondaire sur fond uni | Même règle que `outline` : choisir l'une ou l'autre pour tout le produit, pas les deux dans un même groupe. |
| `ghost` | Action à faible poids (barre d'outils, en-tête de carte) | Libellé obligatoire. Jamais seul en bas d'un formulaire. |
| `link` | Action présentée comme un lien dans un texte | Pour une navigation, utiliser `asChild` avec un `<a>`. |

| Taille | Hauteur | Règle |
|---|---|---|
| `sm` | `size.8` | Zones denses : tableaux, barres d'outils, filtres. |
| `default` | `size.9` | Cas général : formulaires, modales, cartes. |
| `lg` | `size.10` | Action principale isolée : page d'accueil, écran vide, fin de parcours. |

| État | Comportement |
|---|---|
| Repos | Le bouton est cliquable et atteignable au clavier (Tab). |
| Survol | Le fond change de teinte (ou apparaît pour `ghost` et `outline`, soulignement pour `link`) pour confirmer que l'élément est cliquable. Aucun changement de taille, pour ne pas déplacer la mise en page. |
| Focus | Un anneau de 3 px apparaît autour du bouton, uniquement à la navigation clavier (`:focus-visible`). Entrée ou Espace déclenche l'action. |
| Désactivé | Le bouton passe à 50 % d'opacité, ne réagit plus au clic ni au survol et sort de l'ordre de tabulation. À réserver aux actions impossibles dans le contexte (ex : droits insuffisants), avec une explication à proximité. |

## Tokens utilisés

| Partie | État | Tokens |
|---|---|---|
| `container` | toutes | hauteur `size.8` / `size.9` / `size.10` selon la taille ; marge horizontale `spacing.3` / `spacing.4` / `spacing.6` ; espace entre icône et libellé `spacing.1-5` (sm) ou `spacing.2` ; arrondi `radius.md` |
| `container` · default | repos / survol | fond `color.bg.primary` / `color.bg.primary-hover` |
| `container` · destructive | repos / survol | fond `color.bg.destructive` / `color.bg.destructive-hover` |
| `container` · outline | repos / survol | fond `color.bg.default` → `color.bg.accent` ; contour `color.strokes.default` |
| `container` · secondary | repos / survol | fond `color.bg.secondary` / `color.bg.secondary-hover` |
| `container` · ghost | repos / survol | aucun fond → `color.bg.accent` |
| `container` · link | toutes | aucun fond |
| `label` · default | toutes | texte `color.text.on-primary` |
| `label` · destructive | toutes | texte `color.text.on-destructive` |
| `label` · outline, ghost | repos / survol | texte `color.text.default` → `color.text.on-accent` |
| `label` · secondary | toutes | texte `color.text.on-secondary` |
| `label` · link | repos / survol | texte `color.text.link`, souligné au survol |
| `icon` | toutes | même logique que le libellé : `color.icon.on-primary`, `color.icon.on-destructive`, `color.icon.default` → `color.icon.on-accent`, `color.icon.on-secondary`, `color.icon.link` |
| `focus-ring` | focus | anneau `color.strokes.focus-ring` (`color.strokes.error-ring` pour `destructive`) ; contour `color.strokes.focus` pour `outline` |
| `container` | désactivé | opacité 50 % sur l'ensemble, sans token de couleur dédié |

Typographie : style `text-sm-medium` (`text-sm-medium-underline` au survol de `link`). Ombre : style `shadow-xs` sur `default`, `destructive`, `outline` et `secondary`.

## Accessibilité

- Élément natif : `<button>`. Avec `asChild`, l'élément enfant (`<a>`, `Link`) remplace le `<button>` et garde sa sémantique.
- Clavier : atteignable avec Tab ; Entrée et Espace déclenchent l'action. Dans un formulaire, préciser `type="button"` pour toute action qui ne soumet pas, sinon Entrée dans un champ la déclenche.
- Focus : anneau de 3 px visible uniquement au clavier (`:focus-visible`), jamais supprimé avec `outline: none` sans remplacement.
- Contraste : libellé / fond ≥ 4,5:1 pour toutes les variantes, en Light et en Dark ; anneau de focus ≥ 3:1 avec le fond de la page. L'état désactivé est exempté, mais ne doit pas porter d'information essentielle.
- Icônes : décoratives (`aria-hidden`) quand un libellé est présent. Le libellé reste le nom accessible.
- Zone de clic : `sm` (32 px) seulement sur desktop dense ; sur mobile, préférer `default` ou `lg`.

## Exemples

```tsx
import { Button } from "@/components/ui/button"
import { Plus, ArrowRight, Trash2 } from "lucide-react"

// Action principale d'un formulaire
<Button type="submit">Enregistrer</Button>

// Action principale + action secondaire
<div className="flex justify-end gap-2">
  <Button variant="outline" type="button">Annuler</Button>
  <Button type="submit">Créer le projet</Button>
</div>

// Action irréversible (ouvre une confirmation)
<Button variant="destructive" onClick={openConfirmDialog}>
  <Trash2 /> Supprimer le compte
</Button>

// Action à faible poids dans une barre d'outils
<Button variant="ghost" size="sm">
  <Plus /> Ajouter un filtre
</Button>

// Fin de parcours, avec icône à droite
<Button size="lg">
  Continuer <ArrowRight />
</Button>

// Navigation : un vrai lien avec le style du bouton
<Button variant="link" asChild>
  <a href="/aide">Consulter l'aide</a>
</Button>

// Action impossible dans le contexte, avec explication
<Button disabled aria-describedby="droits">Publier</Button>
<p id="droits">Seuls les administrateurs peuvent publier.</p>
```

## Do et Don't

- **Do :** un seul `default` par zone, placé à droite du groupe.
- **Don't :** deux `default` côte à côte, ou `default` + `destructive` de même poids.
- **Do :** un verbe qui annonce le résultat : « Créer le projet ».
- **Don't :** « OK », « Valider », « Cliquez ici ».
- **Do :** `destructive` suivi d'une confirmation qui reprend l'objet supprimé.
- **Don't :** `destructive` pour une action réversible (masquer, archiver).
- **Do :** `asChild` avec `<a>` pour naviguer.
- **Don't :** `onClick={() => router.push(...)}` sur un `Button` pour changer de page.
- **Do :** des couleurs par token sémantique (`color.bg.primary`).
- **Don't :** une couleur en dur ou une classe Tailwind de palette (`bg-red-600`) sur le bouton.

---

Les sections suivantes complètent le template de la formation.

## Anatomie

| Partie | Rôle |
|---|---|
| `container` | Zone cliquable : porte le fond, le contour, l'arrondi, l'ombre et les marges. |
| `icon` (gauche) | Icône optionnelle avant le libellé, pour renforcer le sens de l'action (Ex : `Plus` pour « Ajouter »). 16 px. |
| `label` | Texte de l'action. Obligatoire. |
| `icon` (droite) | Icône optionnelle après le libellé, pour indiquer une suite (Ex : `ArrowRight` pour « Continuer »). 16 px. |
| `focus-ring` | Anneau de 3 px autour du container, visible uniquement au focus clavier. |

## Correspondance avec Figma

| Dans Figma | Dans le code |
|---|---|
| Composant `Button` | `<Button>` |
| `Variant=Default` · `Destructive` · `Outline` · `Secondary` · `Ghost` · `Link` | `variant="default"` · `"destructive"` · `"outline"` · `"secondary"` · `"ghost"` · `"link"` |
| `Size=Small` · `Default` · `Large` | `size="sm"` · `"default"` · `"lg"` |
| `State=Hover` | `:hover` (CSS, pas de prop) |
| `State=Focus` | `:focus-visible` (CSS, pas de prop) |
| `State=Disabled` | `disabled` |
| Propriété `Label` | `children` (texte) |
| `Icon left` / `Icon right` (booléens) | icône placée avant / après le texte dans `children` |
| `Icon left · glyph` / `Icon right · glyph` | composant d'icône `lucide-react` choisi (Ex : `<Plus />`) |
| Composant `Button Icon` | `ButtonIcon` (voir sa fiche) |
| Variables `BG/…`, `Text/…`, `Icon/…`, `Strokes/…` | tokens `color.bg.…`, `color.text.…`, `color.icon.…`, `color.strokes.…` |

## Limites connues

- Pas d'état **loading** : pour une action longue, désactiver le bouton et ajouter une icône `Loader` animée à la main, en attendant une variante dédiée.
- Taille par défaut différente : `Size=Small` dans Figma, `size="default"` dans le code. Toujours choisir la taille explicitement dans Figma.
- Les tokens `color.bg.primary-hover`, `color.bg.secondary-hover` et `color.bg.destructive-hover` n'existent pas dans shadcn d'origine (qui utilise `bg-primary/90`). Ils doivent être déclarés dans le thème du code.
- `secondary` et `outline` jouent le même rôle : le produit doit en choisir une comme norme pour les actions secondaires.
- Les styles de texte et l'ombre `shadow-xs` sont encore importés d'un autre fichier Figma.

## Implémentation de référence

[`src/components/ui/button.tsx`](../../src/components/ui/button.tsx)
