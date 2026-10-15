# Filament Dry Box Example

A small example project built with the EC Chamber method, which it installs as the package `@ec-chamber/method` from [env-control-chamber](https://github.com/JGulley13/env-control-chamber). It models a filament dry box: a sealed chamber with humidity and temperature sensors, a heater, and a desiccant cartridge, together with its stakeholders, requirements, and verification cases.

## Setup

1. Start the local registry (the course `verdaccio` repository) and make sure `@ec-chamber/method` is published to it.
2. Install the method into this repository:
   ```bash
   oml install
   ```
   The registry is set in `.oml/settings.yml`. The package is installed into `deps/@ec-chamber/method/`.

## Model

| File | Content | How it was authored |
|---|---|---|
| `src/oml/example.com/dry-box/stakeholders.oml` | Maker, Safety Officer | OML text (Sierra `stakeholder` vocabulary) |
| `src/oml/example.com/dry-box/components.oml` | Dry box chamber, sensors, heater, desiccant, humidity and temperature conditions | OML text (method `environment` vocabulary) |
| `src/oml/example.com/dry-box/requirements.oml` | Requirements | Through `src/md/Requirements.md` |
| `src/oml/example.com/dry-box/verifications.oml` | Verification cases | Through `src/md/Verifications.md` |
| `src/oml/example.com/dry-box/codegen.oml` | `matrix` codegen config | OML text |

## Use

Open this repository in OML Code and open the pages in `src/md` in the OML Markdown Preview. Both pages compose editor templates from the installed package:

- `Requirements.md` uses the Sierra Requirements editor.
- `Verifications.md` uses the method's Verification editor, with its rule that a Passed or Failed case must cite evidence.

Then generate the Requirements Verification Matrix with the installed generator:

```bash
oml lint
oml codegen -c matrix
```

It writes `build/docs/VerificationMatrix.md`: a verdict summary, a traceability table, one section per requirement with its verification cases, and the coverage gaps.

## Upgrading the method

A plain `oml install` keeps the installed version. To move to a newer one, name it:

```bash
oml install @ec-chamber/method@^0.1.1
```
