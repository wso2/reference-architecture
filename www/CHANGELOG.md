## Changelog

### v0.13.0

- added option to disable table of contents in a page-specific manner with page metadata setting `disable_toc: true`
- bugfix: fixed Google Analytics JavaScript in builds when this is defined in settings

### v0.12.3

- bugfix: fixed navigation links to address changes that were released in mkdocs v1.0

### v0.12.2

- bugfix: added mock setting to the `mkdocs_theme.yml` file to address an upstream mkdocs bug that occurs when this file is blank (issue #46)

### v0.12.1

- bugfix: added `*.yml` to MANIFEST.in file to support new yml settings file required for mkdocs v1.0+

### v0.12.0

- added `mkdocs_theme.yml` file to support mkdocs v1.0 settings file changes

### v0.11.0

- added support for Gitlab icon in navigation menus

### v0.10.2

- Fix the templates in base.html that have been changed in mkdocs 0.17

### v0.10.1

- added responsive image support

### v0.10.0

- added support for MkDocs v0.17 changes
- updated FontAwesome to v4.7.0

### v0.9.4

- added support for H3 header titles in sidebar menu (PR #9)

### v0.9.3

- Added support for > 2 level dropdown link depth (Issue #1 with PR #3)
- Updated Hack web fonts to v2.018

### v0.9.2

- Updated Hack web fonts to v2.015.


### v0.9.1

- modified the width of the footer horizontal line to avoid overlap with long TOC in the left sidebar
- minified the Bootstrap CSS
- modified the formatting of license declaration displays in the footer

### v0.9.0

- Initial release
