# Todo List

A personal tracker for projects, goals, weekly and daily planning. It runs as a web page you can install on your phone and laptop, and it syncs through **one JSON file in a private GitHub repo that you own**.

- The app (these files) goes in a **public** repo and is served by GitHub Pages. It contains no personal data.
- Your data goes in a separate **private** repo. Only your access token can read or write it.

## 1. Publish the app

1. On GitHub, create a new **public** repository, for example `todo-list`.
2. Upload everything in this folder: `index.html`, `manifest.webmanifest`, `sw.js`, `README.md` and the `icons` folder. (On the repo page: **Add file › Upload files**, drag them in, **Commit changes**.)
3. Go to **Settings › Pages**. Under **Build and deployment**, set Source to **Deploy from a branch**, Branch to **main** and folder **/ (root)**, then **Save**.
4. After a minute your app is at `https://YOUR-USERNAME.github.io/todo-list/`.

## 2. Make the private data repo

1. Create a new repository named `todo-list-data`.
2. Set it to **Private**.
3. Tick **Add a README file** (so the repo has a `main` branch to save into).

## 3. Make an access token

1. GitHub › your avatar › **Settings › Developer settings › Personal access tokens › Fine-grained tokens › Generate new token**.
2. Name: `todo-list`. Expiration: pick a date and put a reminder in your calendar to renew it.
3. **Repository access:** *Only select repositories* › `todo-list-data`.
4. **Permissions › Repository permissions › Contents:** *Read and write*. Leave everything else as is.
5. Generate, then copy the token (starts with `github_pat_`). GitHub only shows it once; keep it in your password manager.

## 4. Connect and bring your data over

1. In the Claude version of the tracker, open **Weekly log** and press **Back up everything (.json)**.
2. Open your app link, go to **Sync & backup**, enter your username, `todo-list-data` and the token, then **Connect**.
3. Press **Import a backup (.json)** and choose the file from step 1.

## 5. Install it

- **iPhone:** open the link in Safari › Share › **Add to Home Screen**. Open it from the new icon and connect again in **Sync & backup** (the home-screen app keeps its own storage, separate from Safari).
- **Mac:** Safari › File › **Add to Dock**, or in Chrome/Edge use the install icon in the address bar.
- **Siri quick add:** in Shortcuts, make a shortcut with **Open URLs** › `https://YOUR-USERNAME.github.io/todo-list/#add`.

## How sync works

- Every change is saved on the device first, so the app works offline.
- A few seconds after a change, and every minute while it's open, the app pulls the file from GitHub, merges it item by item (the newest edit of each task wins), and saves it back. Each save is a commit, so the repo keeps a full history you can roll back to.
- Editing the same task on two devices within a minute keeps the later edit.

## Updating the app

Replace `index.html` in the public repo. Also open `sw.js` and change `VERSION` (e.g. `todo-v1` → `todo-v2`) so installed copies pick up the new version. Your data isn't touched.

## If something goes wrong

- **Lost a device:** delete the token on GitHub (Settings › Developer settings), make a new one, and paste it into your other devices.
- **"Sync problem"** in the sidebar: open **Sync & backup** to see the message. Expired tokens are the usual cause.
- **Moving away from this app:** your data is the readable `tracker.json` in your private repo, and **Download backup** gives you the same file anytime.
