# Applications supportées / Supported apps

## Français

| Application | Interface | Type de patch | État |
|---|---|---|---|
| **Reasonix Studio 2.40.0** | `resources\frontend-next\dist` (plain) | copie de `voice-input.js` + une balise `<script>` | validé (micro, clé, envoi, file) |
| **AionUi 2.2.2** | `resources\app.asar` | repack asar avec `--unpack-dir` / `--unpack`, préservation de `app.asar.unpacked` | validé sur Windows ; dépôt `AiTron-Voice-Input` |
| **Open Cowork** | application Electron | même module + sélecteurs | base d'origine ; dépôt `AiTron-Voice-Input` |

**La méthode est la même** : repérer le composeur, l'envoi et l'arrêt ; déterminer si l'UI est
plain ou dans un asar ; adapter le stockage et le preload ; ancrer le micro ; vérifier ; garder
un retour arrière ; documenter. Voir [`METHODOLOGY.md`](METHODOLOGY.md) (EN) /
[`DEMARCHE.md`](DEMARCHE.md) (FR).

## English

| App | UI | Patch type | State |
|---|---|---|---|
| **Reasonix Studio 2.40.0** | `resources\frontend-next\dist` (plain) | copy `voice-input.js` + one `<script>` tag | validated (mic, key, send, queue) |
| **AionUi 2.2.2** | `resources\app.asar` | asar repack with `--unpack-dir` / `--unpack`, preserve `app.asar.unpacked` | validated on Windows; repo `AiTron-Voice-Input` |
| **Open Cowork** | Electron app | same module + selectors | original base; repo `AiTron-Voice-Input` |

**The method is the same**: locate the composer/send/stop, determine plain vs asar, adapt
storage and preload, anchor the mic, verify, keep a rollback, document. See
[`METHODOLOGY.md`](METHODOLOGY.md) (EN) / [`DEMARCHE.md`](DEMARCHE.md) (FR).
