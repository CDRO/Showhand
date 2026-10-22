# Showhand

Presentations and quizzes for workshops and meetings, straight from a folder in your browser:
no installation, no server, no admin rights, no internet. Presenter console on your screen, audience window on the
projector; quiz answers stay hidden until you reveal them.

## Download

Get `Showhand-<version>.zip` from the [releases](../../releases) (or the newest workflow artifact), unpack it and
double-click `index.html`. The `README.md` inside the ZIP explains the rest; the app has a help in English and German.

## This repository

Only the ZIPs are published here. The app lives in [CDRO/Showhand-core](https://github.com/CDRO/Showhand-core)
(npm package `@showhand/core`); this repository builds the ZIP from it, tests exactly what goes into the ZIP by
opening it via `file://` in Chromium, and attaches it to a release.

```sh
npm ci
npm run build    # → dist/Showhand
npm test         # end-to-end test of dist/Showhand (needs: npx playwright install chromium)
```

### Access to the core

CDRO/Showhand-core is private. The workflow needs the repository secret **`CORE_TOKEN`**: a fine-grained personal
access token with *Contents: read* on CDRO/Showhand-core (Settings → Secrets and variables → Actions). Once
`@showhand/core` is on npm, the token is no longer needed.

### Making a release

- Push a tag `v1.2.3`, or
- run the workflow *Build, test and publish the ZIP* by hand with a version.

### Which core goes in

`package.json` pins `@showhand/core`. Until the package is on npm it comes straight from GitHub
(`github:CDRO/Showhand-core#main`; `package-lock.json` pins the exact commit, `npm update @showhand/core`
moves it forward). Once `@showhand/core` is published, switch to a version range such as `"^0.1.0"`.

## Licence

MIT

## Credits

The hand in the logo and the social image is "Raised hand" from [Fluent Emoji](https://github.com/microsoft/fluentui-emoji) © Microsoft, MIT License – see
[THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).
