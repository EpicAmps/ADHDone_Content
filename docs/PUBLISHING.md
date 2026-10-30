# Publishing content

1. Edit JSON in `content/`, retaining stable IDs for existing items.
2. Validate syntax and schema using `schemas/content.schema.json`; check that guided step durations total the declared duration.
3. Increment `contentVersion` in `manifest.json` for every release.
4. Only use supported template types; new native behavior requires an app release.
5. Publish to the default branch after review. The iOS client should fetch the manifest from a stable static/CDN endpoint, not GitHub's authenticated API.
6. Test with an offline cache and older app versions. The client should reject invalid/incompatible updates and keep the last known good content.

## Compatibility
`schemaVersion` identifies the JSON contract; `minimumAppVersion` gates incompatible app builds. Item IDs must remain stable for bookmarks, preferences, and eventual analytics. Never publish secrets or user information in this public repository.

## Hosting decision
A stable public static URL or CDN for the manifest and files is **TBD**. Do not embed a GitHub API token in the iOS app. Consider automated validation and static deployment once the client is implemented.
