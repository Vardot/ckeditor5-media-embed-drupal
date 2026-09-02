# CKEditor 5 Media embed, for Drupal

This repository packages the **build output** of the
[`@ckeditor/ckeditor5-media-embed`](https://www.npmjs.com/package/@ckeditor/ckeditor5-media-embed)
plugin as a Composer `drupal-library`, so `drupal/ckeditor_media_embed` can require it the way
`drupal/anchor_link` requires
[`vardot/ckeditor5-anchor-drupal`](https://github.com/Vardot/ckeditor5-anchor-drupal) — with
Composer, rather than a Drush download or a copy out of `node_modules`.

Only what Drupal serves is shipped: `build/`, the `lang/` contexts and `theme/`.

## Installation

```bash
composer require vardot/ckeditor5-media-embed-drupal
```

`drupal/ckeditor_media_embed` loads the plugin from
`libraries/ckeditor5/plugins/media-embed/build/media-embed.js`, so the consuming project maps
this package there explicitly:

```json
"extra": {
  "installer-paths": {
    "web/libraries/ckeditor5/plugins/media-embed": [
      "vardot/ckeditor5-media-embed-drupal"
    ]
  }
}
```

## Versioning — match Drupal core's CKEditor 5

**A CKEditor 5 plugin must be built against the same CKEditor 5 version Drupal core bundles.**
Mixing minors makes the editor fail with `ckeditor-duplicated-modules`. Read core's version from
`web/core/core.libraries.yml` (the `ckeditor5:` entry) and require the tag that matches it:

| Drupal core | CKEditor 5 in core | Require |
|---|---|---|
| 11.4.x | 47.6.2 | `~47.6.2` |

## Licence, and why not the LTS line

Tags here are built **only from GPL dual-licensed CKEditor 5 releases**.

CKEditor 5 releases from 47.7.0 on that line are the **Long Term Support edition**, which CKSource
publishes under a **commercial licence only** — there is no GPL option, so they cannot be
redistributed here or shipped in a GPL-2.0-or-later Drupal distribution. `47.6.2` is the last
GPL dual-licensed release of the 47.6 line, and it is the one Drupal 11.4 core bundles.

See [LICENSE.md](LICENSE.md) — GNU General Public License Version 2 or later, or commercial terms
from CKSource. © 2003–2026 CKSource Holding sp. z o.o.

## Upstream

- Source: https://github.com/ckeditor/ckeditor5 (`packages/ckeditor5-media-embed`)
- Documentation: https://ckeditor.com/docs/ckeditor5/latest/features/media-embed.html

## Maintainers

- [Vardot](https://github.com/vardot)
