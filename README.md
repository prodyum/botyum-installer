# Botyum iOS Installer

This repository is the GitHub Pages OTA installer for the latest signed Botyum Ad Hoc IPA:

```text
https://prodyum.github.io/botyum-installer/
```

OneLane owns the publish flow. From the parent source repository, `./.ol/ol.cmd` rebuilds and publishes the selected app; `./.ol/ol.cmd publish --github-page` republishes already prepared installer content.

## Published Contract

```text
index.html
manifest.plist
manifest.webmanifest
release.json
assets/icon-192.png
assets/icon-512.png
ipa/botyum-install.ipa
ipa/botyum-install.metadata.json
```

`manifest.plist` drives Safari's `itms-services` installation. `release.json` binds the public page to IPA, manifest, source commit, workflow run, and content hashes; OneLane waits until GitHub Pages serves that exact marker.

Installation works only on iPhone or iPad devices whose UDIDs were included in the Ad Hoc profile when this IPA was signed.
