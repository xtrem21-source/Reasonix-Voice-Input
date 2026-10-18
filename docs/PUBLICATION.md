# Publication — checklist / Checklist

## Français

| Point | État |
|---|---|
| Nom du dépôt | **`Reasonix-Voice-Input`** |
| Compte | **`xtrem21-source`** (vérifié : `git ls-remote` répond et le credential Git local existe) |
| Visibilité | **privé** |
| Licence | **MIT** (`LICENSE`) |
| Documentation | FR/EN : README, tutoriel, inspection, méthode, problèmes/solutions, version, journal, changelog, sécurité, publication, applications supportées |
| `index.html` de l'application | **non livré** : fichier tiers, licence de l'app non documentée ; recréable localement (voir `docs/reference/README.md`) |
| Chemins personnels | masqués (`%LOCALAPPDATA%`, `$env:USERPROFILE`) |
| Secrets | aucun (clé Gemini saisie par l'utilisateur) |
| Historique | **export propre** depuis l'arbre de travail, sans l'HTML de l'app |
| Avertissement | projet **non officiel**, non affilié, sans garantie, peut casser à chaque mise à jour |

### Export propre

Le dépôt local `Reasonix-Voice-Input` garde son historique (qui contient encore l'HTML de
l'app). L'export publiable est un dossier séparé `Reasonix-Voice-Input-publish`, sans `.git`,
sans `logs/`, sans `old/` (sauf `.gitkeep`), sans `docs/reference/ReasonixStudio-*.html`.

```powershell
cd $env:USERPROFILE\Desktop\open-cowork-micro\Reasonix-Voice-Input-publish
git remote add origin https://github.com/xtrem21-source/Reasonix-Voice-Input.git
git push -u origin main
```

Avec GitHub CLI (si le dépôt n'existe pas encore) :

```powershell
gh repo create xtrem21-source/Reasonix-Voice-Input --private --source . --remote origin --push
```

Le dépôt privé `xtrem21-source/Reasonix-Voice-Input` est **publié** (branche `main`,
commit `3d44a1c`, 2026-10-18) et accessible avec le credential Git local.

## English

| Item | State |
|---|---|
| Repository name | **`Reasonix-Voice-Input`** |
| Account | **`xtrem21-source`** (verified: `git ls-remote` answers and the local Git credential exists) |
| Visibility | **private** |
| License | **MIT** (`LICENSE`) |
| Documentation | FR/EN: README, tutorial, inspection, method, problems/solutions, version, journal, changelog, security, publication, supported apps |
| App `index.html` | **not shipped**: third-party file, app license undocumented; recreate locally (see `docs/reference/README.md`) |
| Personal paths | sanitized (`%LOCALAPPDATA%`, `$env:USERPROFILE`) |
| Secrets | none (Gemini key entered by the user) |
| History | **clean export** from the working tree, without the app HTML |
| Disclaimer | **unofficial**, not affiliated, no warranty, may break on every update |

### Clean export

The local `Reasonix-Voice-Input` repo keeps its history (which still contains the app HTML).
The publishable export is a separate `Reasonix-Voice-Input-publish` folder, without `.git`,
without `logs/`, without `old/` (except `.gitkeep`), without
`docs/reference/ReasonixStudio-*.html`.

```powershell
cd $env:USERPROFILE\Desktop\open-cowork-micro\Reasonix-Voice-Input-publish
git remote add origin https://github.com/xtrem21-source/Reasonix-Voice-Input.git
git push -u origin main
```

With GitHub CLI (if the repo does not exist yet):

```powershell
gh repo create xtrem21-source/Reasonix-Voice-Input --private --source . --remote origin --push
```

The private `xtrem21-source/Reasonix-Voice-Input` repository is **published** (`main` branch,
commit `3d44a1c`, 2026-10-18) and accessible with the local Git credential.
