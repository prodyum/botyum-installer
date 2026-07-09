# Botyum Installer Site

This directory is the `prodyum/botyum-installer` GitHub Pages submodule. It hosts the static iOS installer page for the latest Botyum IPA.

## Purpose

An Ad Hoc iOS IPA is only useful to registered devices if testers have a simple install entry point. This site provides that entry point:

```text
https://prodyum.github.io/botyum-installer/
```

The page links to the manifest and IPA required by iOS OTA installation.

## Files

```text
index.html                 Installer page
manifest.plist             iOS OTA manifest
release.json               Current release marker and content hashes
manifest.webmanifest       Web metadata for the installer page
assets/                    Icons and static assets
ipa/botyum-install.ipa     Latest signed IPA
```

`botyum-install.ipa` is replaced by the OneLane release workflow after a successful GitHub Actions iOS build. `release.json` is regenerated for the same release and is used by OneLane to verify that GitHub Pages is serving the exact current installer content.

## Publish Flow

The full release command publishes this site automatically:

```powershell
.\ol-botyum.cmd
```

To publish only the current installer site content:

```powershell
.\ol-gp.cmd
```

`ol-gp.ps1` commits and pushes this submodule, then waits until GitHub Pages serves the expected installer content.

## Tester Requirements

The installer is intended for iPhone or iPad devices whose UDIDs are included in the active Ad Hoc provisioning profile. If a device is not registered in Apple Developer resources before the IPA is built, iOS will not install that package on that device.
