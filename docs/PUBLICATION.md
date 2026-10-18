# Publication — checklist / Checklist

## Français

| Point | État |
|---|---|
| Nom du dépôt | **`Reasonix-Voice-Input`** |
| Compte supposé | `Xtrem-21` (adresse GitHub des commits) — à confirmer |
| Licence | **MIT** (`LICENSE`) |
| Documentation | FR/EN : README, tutoriel, inspection, méthode, problèmes/solutions, version, journal, changelog, sécurité |
| `index.html` de l'application | **non livré** : fichier tiers, licence de l'app non documentée ; recréable localement (voir `docs/reference/README.md`) |
| Chemins personnels | masqués (`%LOCALAPPDATA%`) |
| Secrets | aucun (clé Gemini saisie par l'utilisateur) |
| Historique | **export propre** depuis l'arbre de travail, sans l'HTML de l'app |
| Visibilité recommandée | **privé d'abord**, public après quelques jours de test |
| Avertissement | projet **non officiel**, non affilié, sans garantie, peut casser à chaque mise à jour |

### Export propre

Le dépôt local `Reasonix-Voice-Input` garde son historique (qui contient encore l'HTML de
l'app). L'export publiable est un dossier séparé `Reasonix-Voice-Input-publish`, sans `.git`,
sans `logs/`, sans `old/` (sauf `.gitkeep`), sans `docs/reference/ReasonixStudio-*.html`.

```powershell
cd $env:USERPROFILE\Desktop\open-cowork-micro\Reasonix-Voice-Input-publish
git remote add origin https://github.com/Xtrem-21/Reasonix-Voice-Input.git
git push -u origin main
```

Avec GitHub CLI (si le dépôt n'existe pas encore) :

```powershell
gh repo create Xtrem-21/Reasonix-Voice-Input --private --source . --remote origin --push
```

> **Rien n'est publié tant que l'utilisateur n'a pas donné son GO.**

## English

| Item | State |
|---|---|
| Repository name | **`Reasonix-Voice-Input`** |
| Assumed account | `Xtrem-21` (commit GitHub address) — to confirm |
| License | **MIT** (`LICENSE`) |
| Documentation | FR/EN: README, tutorial, inspection, method, problems/solutions, version, journal, changelog, security |
| App `index.html` | **not shipped**: third-party file, app license undocumented; recreate locally (see `docs/reference/README.md`) |
| Personal paths | sanitized (`%LOCALAPPDATA%`) |
| Secrets | none (Gemini key entered by the user) |
| History | **clean export** from the working tree, without the app HTML |
| Recommended visibility | **private first**, public after a few days of testing |
| Disclaimer | **unofficial**, not affiliated, no warranty, may break on every update |

### Clean export

The local `Reasonix-Voice-Input` repo keeps its history (which still contains the app HTML).
The publishable export is a separate `Reasonix-Voice-Input-publish` folder, without `.git`,
without `logs/`, without `old/` (except `.gitkeep`), without
`docs/reference/ReasonixStudio-*.html`.

```powershell
cd $env:USERPROFILE\Desktop\open-cowork-micro\Reasonix-Voice-Input-publish
git remote add origin https://github.com/Xtrem-21/Reasonix-Voice-Input.git
git push -u origin main
```

With GitHub CLI (if the repo does not exist yet):

```powershell
gh repo create Xtrem-21/Reasonix-Voice-Input --private --source . --remote origin --push
```

> **Nothing is published until the user gives the GO.**
