# Release manifest format

`releases.json` is the canonical index for official APK assets. A release is
added only after its signed APK and matching checksum asset have been uploaded
to a GitHub Release.

```json
{
  "schema": 1,
  "product": "evDash",
  "packageId": "sk.next176.evdashapp",
  "releases": [
    {
      "version": "1.3.10",
      "build": 935,
      "tag": "v1.3.10-935",
      "publishedAt": "2026-09-16T00:00:00Z",
      "apk": "evdash-1.3.10-935.apk",
      "sha256": "64 lowercase hexadecimal characters",
      "downloadUrl": "https://github.com/NEXT176-s-r-o/evdash-releases/releases/download/v1.3.10-935/evdash-1.3.10-935.apk",
      "notes": "Short owner-facing summary."
    }
  ]
}
```

Rules:

1. The APK is built and signed outside this repository.
2. The APK filename, build number, Git tag, SHA-256 and manifest entry must
   agree.
3. The same release must contain a text file named
   `<apk filename>.sha256`, with the hash and filename.
4. Never replace an existing APK or mutate a published manifest entry. Publish a
   new release instead.
5. A regional mirror may download the GitHub asset and serve it only after
   checking its SHA-256 against this manifest.
