# Upgrade jQuery & Bootstrap — patch changelog

Summary
- Replaced local jQuery 1.11.0 with CDN-hosted jQuery 3.7.1 (added SRI + crossorigin)
- Added jQuery Migrate 3.6.0 to help compatibility with older 1.x APIs
- Replaced local Bootstrap JS with CDN-hosted Bootstrap 3.4.1 (added SRI + crossorigin)
- Added a testing guidance comment to `_includes/js.html`
- Escaped template meta variables in `_includes/head.html` (`| escape`) to reduce XSS risk
- Added `rel="noopener noreferrer"` to social links in `_includes/header.html` to mitigate reverse tabnabbing

Files changed
- `_includes/js.html` — replace local scripts with CDN ones, add notes
- `_includes/head.html` — use `| escape` on site meta variables
- `_includes/header.html` — add `rel` attribute to external links

How to apply the patch
1. Save the patch files in your repo (e.g., `patches/upgrade-jquery-bootstrap.patch` and `patches/upgrade-jquery-bootstrap-changes.patch`).
2. Apply them locally:

   git apply patches/upgrade-jquery-bootstrap.patch
   git apply patches/upgrade-jquery-bootstrap-changes.patch

3. Verify changes and commit:

   git add _includes/js.html _includes/head.html _includes/header.html
   git commit -m "chore: upgrade jQuery to 3.7.1 and Bootstrap to 3.4.1 (CDN); add small security fixes"

Notes
- I included jQuery Migrate as a temporary compatibility measure. Remove it after confirming compatibility.
- Consider upgrading Bootstrap to 4/5 in a follow-up PR if you are ready to update markup/CSS.
- I can open a PR for you if you provide GH credentials (`gh` CLI or a token) or if you'd like me to prepare the PR body and title for you to paste.
