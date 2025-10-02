# Minecraft Default Assets
[![Generate Assets](https://github.com/Resourcepack-Registry/default/actions/workflows/generate_assets.yml/badge.svg)](https://github.com/Resourcepack-Registry/default/actions/workflows/generate_assets.yml)
[![Latest Release](https://github.com/Resourcepack-Registry/default/blob/badge/latest_release.svg?raw=true)](https://github.com/Resourcepack-Registry/default/tree/latest-release)
[![Latest Snapshot](https://github.com/Resourcepack-Registry/default/blob/badge/latest_snapshot.svg?raw=true)](https://github.com/Resourcepack-Registry/default/tree/latest-snapshot)
[![Compare](https://github.com/Resourcepack-Registry/default/blob/badge/compare.svg?raw=true)](https://github.com/Resourcepack-Registry/default/compare/latest-release...latest-snapshot)

<img align="right" width="128" height="128" alt="image" src="https://github.com/user-attachments/assets/233905c0-2913-4c68-8854-74a96d18bb39" />

This repository keeps track of Minecrafts generated default assets for a resourcepack vor every version since version [`rd-132211`](https://minecraft.wiki/w/Java_Edition_pre-Classic_rd-132211). Every 12 hours a check is made to see if there is a new Minecraft version. If a new version is available, it will be published on the `generated` branch with the corresponding tag of the version.

## Structure
Individual files can be accessed by the respective version tag:
```url
https://github.com/Resourcepack-Registry/default/blob/<version>/<path to file>?raw=true
```

Or to view the latest assets, there is a [`latest-release`](https://github.com/Resourcepack-Registry/default/tree/latest-release) and [`latest-snapshot`](https://github.com/Resourcepack-Registry/default/tree/latest-snapshot) tag:
```url
https://github.com/Resourcepack-Registry/default/blob/latest-release/<path to file>?raw=true

https://github.com/Resourcepack-Registry/default/blob/latest-snapshot/<path to file>?raw=true
```

## How it works
```mermaid
flowchart TD
    START((Start))
    --> 
    A[Get latest **Version**<br>from Manifest]
    --> 
    B[Check for existing<br>**Snapshot** tag]
    -->
    TAG_EXISTS{Tag exists}
    -->
    |No| TAG_EXISTS_NO-A[Download new<br>**Snapshot** Assets]
    -->
    TAG_EXISTS_NO-B[**Add** corresponding<br>version tag]
    -->
    TAG_EXISTS_NO-C[Check if<br>**Snapshot == Release**]
    -->
    TAG_EXISTS_NO-EQUAL{Equal}
    -->
    |Yes| TAG_EXISTS_NO-EQUAL_YES-A[**Remove** old<br>'latest-release' tag]
    -->
    TAG_EXISTS_NO-EQUAL_YES-B[**Add** new<br>'latest-release' tag]
    
    TAG_EXISTS_NO-EQUAL
    -->
    |No| TAG_EXISTS_NO-D[**Remove** old<br>'latest-release' tag]
    
    TAG_EXISTS_NO-EQUAL_YES-B
    -->
    TAG_EXISTS_NO-D

    TAG_EXISTS_NO-D[**Remove** old<br>'latest-snapshot' tag]
    -->
    TAG_EXISTS_NO-E[**Add** new<br>'latest-snapshot' tag]
    -->
    TAG_EXISTS_NO-F[**Commit** new<br>changes]
    -->
    TAG_EXISTS_NO-G[**Update** badges]

    TAG_EXISTS
    -->
    |Yes| END

    TAG_EXISTS_NO-G
    -->
    END((End))
```

## Disclaimer
This repository assumes that because Mojang intentionally provides a public API for downloading the `client.jar`, they have no objection to the resulting generated assets existing anywhere on the internet for public consumption. If this assumption is ever contradicted, the repository will be removed immediately.
