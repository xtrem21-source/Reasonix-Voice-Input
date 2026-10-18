# Changelog (français)

Les changements notables de ce package sont documentés ici.
Format inspiré de [Keep a Changelog](https://keepachangelog.com/).

## [0.1.2] — 2026-10-18

### Ajouté
- `LICENSE` MIT et avertissement « projet non officiel » dans les deux README.
- Documentation **FR/EN** : inspection, méthode, problèmes/solutions, version, journal,
  changelog, sécurité, publication, applications supportées.
- Méthode **portable en 8 étapes** : le même module s'adapte à d'autres applications Electron
  (AionUi 2.2.2, Open Cowork) ; seuls les sélecteurs, le stockage et le preload changent.

### Modifié
- `docs/INSPECTION-2026-10-18.md` : chemin d'installation masqué
  (`%LOCALAPPDATA%\Programs\Reasonix Studio`).
- `docs/reference/README.md` : l'`index.html` de l'application n'est **pas livré** dans le
  dépôt public ; procédure pour le recréer localement.
- `.gitignore` : ignore la copie locale `docs/reference/ReasonixStudio-*.html`.

### Retiré
- L'`index.html` de Reasonix Studio n'est plus versionné dans l'export public (fichier tiers,
  licence de l'app non documentée).

## [0.1.1] — 2026-10-18

### Ajouté
- **Point de retour garanti** : `PREPARER-SAUVEGARDE-MIC-REASONIX.bat` (`-BackupOnly`) crée
  `index.html.bak` + `index.html.bak.sha256` + une archive datée dans `old/`, **sans patcher**.
- `RESTAURER-MIC-REASONIX.bat` (`-Rollback`) restaure `index.html`, retire `voice-input.js`,
  vérifie l'empreinte, et fonctionne même si Reasonix Studio ne démarre plus.
- Le patcher **vérifie la copie avant toute écriture** et s'arrête en cas de mismatch.
- `-Check` exige désormais une sauvegarde présente et vérifiée.

## [0.1.0] — 2026-10-18

### Ajouté
- Package initial pour **Reasonix Studio 2.40.0**.
- `src/voice-input.reasonix.js` — adaptation d'AiTron Voice Input v5 :
  sélecteurs Reasonix, clés `rx-*`, `reasonixHost.openExternal`, exclusion de `session.stop`,
  composeur `readOnly` accepté, 5 tentatives d'envoi sur ~2 s, ancrage à côté du stop pendant
  une génération.
- `scripts/apply-patch.ps1` — patcher de dossier plain : sauvegarde, injection, hash,
  `-Force`, `-Rollback`, `-Check`. L'application n'est jamais fermée.
- Scripts `.bat`, README FR/EN, inspection, démarche, journal, empreintes, copie de référence.
