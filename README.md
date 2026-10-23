# Margin

A quiet place to write, plan and keep track of things. Margin is a Notion-style note-taking app that runs entirely in your browser. It has no account, no server and no AI, and your notes stay on your device.

**Live app:** https://git-mahmud.github.io/margin/

## Features

**Pages**
- Nested pages and sub-pages in a sidebar tree
- Favorites, and a trash you can restore from
- Emoji page icons and gradient covers
- Breadcrumb navigation

**Block editor**
- Slash menu: type `/` to insert any block
- Block types: text, headings 1–3, to-do, bulleted list, numbered list, toggle, quote, callout, code, divider and sub-page
- Markdown shortcuts: `#`, `##`, `###`, `-`, `1.`, `[]`, `>`, `---` and ` ``` ` followed by a space
- Drag-and-drop reordering, plus a handle menu to delete, duplicate or turn a block into another type
- Inline formatting toolbar: bold, italic, underline, strikethrough, code and links

**Workspace**
- Full-text search with `Ctrl/⌘ + K`
- Light and dark themes
- Installable as an app, and works offline
- Responsive layout for desktop and mobile

## Install as an app

Open the live link in Chrome or Edge and click the **Install** icon in the address bar. On Android, use **⋮ → Install app**. On iPhone or iPad, open the link in Safari and choose **Share → Add to Home Screen**.

## Run locally

Margin is plain HTML, CSS and JavaScript, so there is nothing to build.

1. Download or clone this repository.
2. Open `index.html` in your browser.

Installing as an app and offline caching need the site served over `https://` or `localhost`. To test them locally, run a static server from the project folder:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Deploy with GitHub Pages

1. Push the files to the root of a public repository.
2. Go to **Settings → Pages**.
3. Set the source to **Deploy from a branch**, choose **main** and **/ (root)**, then save.
4. Your site goes live at `https://YOUR-USERNAME.github.io/REPO-NAME/`.

## Project structure

```
.
├── index.html             App markup, styles and logic in one file
├── manifest.webmanifest   App name, colors and icons for installation
├── sw.js                  Service worker for offline use and updates
├── icon-192.png           App icon
├── icon-512.png           App icon
└── README.md
```

## Customize

All code lives in `index.html`:

| To change | Edit |
| --- | --- |
| Colors and theme | The CSS variables at the top of the `<style>` block (`--bg`, `--fg`, `--sb`, `--acc`) |
| Block types in the `/` menu | The `TYPES` array in the script |
| How a block looks | The matching rule in the CSS, for example `.h1 .ce` |
| Block structure and behavior | `blockHTML()` and the keyboard handlers in the script |

## Updating a deployed copy

Commit your changes and GitHub Pages republishes within a couple of minutes. Installed copies pick up the update the next time the app opens, sometimes after a second open. To force every device to drop its old cache, change `margin-v1` to a new name such as `margin-v2` in `sw.js`.

## Your data

Notes are stored in your browser's `localStorage`. Nothing is sent to a server.

- Notes are specific to one browser and one web address, so they don't sync between devices.
- Clearing your browser data erases them.
- Export and import is not available yet, so back up anything important by copying it out.

## Browser support

Current versions of Chrome, Edge, Safari and Firefox. Installing as an app is supported in Chrome, Edge and Safari.

## Roadmap

- Export and import for backups and moving notes between devices
- Table and database views
- Tags
- Page width and font size settings
