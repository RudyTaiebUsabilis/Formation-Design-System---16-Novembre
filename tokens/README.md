# Tokens

Format **W3C Design Tokens (DTCG)** : chaque token a un `$type`, une `$value` et, pour les sémantiques, une `$description`.

| Fichier | Contenu |
|---|---|
| `primitives.tokens.json` | Valeurs brutes : couleurs (`color.neutral.*`, `color.red.*`, `color.alpha.*`), espacements, tailles, rayons. |
| `semantic.light.tokens.json` | Rôles en mode Light, alias vers les primitives : `{color.neutral.900}`. |
| `semantic.dark.tokens.json` | Mêmes rôles, mêmes noms, valeurs du mode Dark. |

Les deux fichiers sémantiques ont **exactement les mêmes noms** : seul l'alias change.

Correspondance avec Figma : collection « DS · Primitives » → `primitives.tokens.json`, collection « DS · Semantics » (modes Light / Dark) → `semantic.*.tokens.json`.

Traduction en CSS : `src/styles/tokens.css` (à générer automatiquement plus tard, par exemple avec Style Dictionary).
