# renovate-config

The shared [Renovate](https://docs.renovatebot.com/) presets for the owner's repositories.

| Preset | Extend it as | For |
| --- | --- | --- |
| `default.json` | `github>dougborg/renovate-config` | every repository |
| `moon.json` | `github>dougborg/renovate-config:moon` | repositories built with [moon](https://moonrepo.dev/), after the default |

A repository's own `renovate.json` extends the default preset and adds only rules specific to that repository:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>dougborg/renovate-config"]
}
```

The policy these presets encode, and why, is recorded in dougborg-dot-net's `docs/decisions/0001-repository-baseline.md`.
The repository is public because the Mend Renovate App cannot read a private preset from a public repository.

Check a change with Renovate's validator before merging it (Node 24.11 or newer; CI runs the same command as the `check` job):

```sh
npx --yes --package=renovate@44.97.4 -- renovate-config-validator --strict --no-global default.json moon.json renovate.json
```
