# Publishing an official Android release

Use this process only on the release machine that holds the evDash signing keystore.
Do not copy the keystore, its passwords or any signing material into this repository,
GitHub Actions, a mirror, email or chat.

Publish only a build approved for public APK distribution. Internal Google Play
testing builds and experimental diagnostic builds do not belong here.

## Required process

Start from an up-to-date main source checkout. Keep Flutter, Android build tools
and GitHub CLI on the release machine. GitHub CLI must have write access to
NEXT176-s-r-o/evdash-releases.

Run scripts/build_android_store.sh. It requests the keystore passwords locally,
rejects a debug or unexpected signing certificate, and writes the signed APK to
build/app/outputs/flutter-apk/app-release.apk. The AAB remains for Google Play;
only the signed APK is used here.

Copy the verified APK to a temporary directory as evdash-VERSION-BUILD.apk and
generate evdash-VERSION-BUILD.apk.sha256 with shasum -a 256. Check the APK signer
again with apksigner verify --verbose --print-certs before any upload.

Create a GitHub Release whose tag is vVERSION-BUILD. Upload exactly two assets:
the APK and its sha256 file. Release title format: evDash VERSION (build BUILD).
Do not overwrite an existing asset or mutate a published build; publish a new
build and tag after a correction.

Then prepend the matching object to releases.json, including version, build, tag,
UTC publication time, APK filename, exact SHA-256, GitHub asset URL and concise
release notes. Point latest.json to the same object. Validate both JSON files
with jq before committing and pushing.

Finally, publish the byte-identical APK through the existing evdash.eu channel
with scripts/publish_apk_release.py. The GitHub asset, manifests and evdash.eu
must all report the same SHA-256.

## China mirror rule

A regional mirror may fetch an APK only from a published GitHub Release and must
check its SHA-256 against releases.json before it serves the file. It must never
build, modify or re-sign evDash.
