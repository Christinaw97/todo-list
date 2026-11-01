# Todo List

A personal tracker for projects, goals, deadlines, and your weekly and daily plan. It's a web page you can install on your phone or laptop. There's no account to create, and nobody (including the person who made this app) can see your tasks.

**Open the app:** https://christinaw97.github.io/todo-list/

## What you can do

- Organize tasks into categories and projects, and set deadlines for tasks or whole goals
- Plan your week and your day, and drag tasks between days
- See everything on a board
- Work offline; changes are saved on your device first
- Install it like an app on iPhone, Android, Mac or Windows
- Sync between devices through a private GitHub repo that you own (optional)

## Quick start (one device, 30 seconds)

1. Open the app link above.
2. On the Welcome screen, press **Start empty**.
3. Add your first task.

Your tasks are saved in that browser on that device. This is fine for trying it out, but read **Back up your data** below.

## Use it on all your devices (about 5 minutes)

To keep your phone and laptop in step, the app saves your tasks as one file in a **private GitHub repository that you own**. You need a free GitHub account. The app talks straight from your browser to your repo, so nothing passes through anyone else.

### 1. Make a private repo for your data

1. On GitHub, click **New repository**.
2. Name it `todo-list-data`.
3. Set it to **Private**.
4. Tick **Add a README file** (this creates the `main` branch the app saves into).
5. Click **Create repository**.

### 2. Make an access token

1. On GitHub, click your avatar, then **Settings › Developer settings › Personal access tokens › Fine-grained tokens › Generate new token**.
2. Name it `todo-list`. Pick an expiration date and put a reminder in your calendar to renew it.
3. Under **Repository access**, choose **Only select repositories** and pick `todo-list-data`.
4. Under **Permissions › Repository permissions**, set **Contents** to **Read and write**. Leave everything else alone.
5. Click **Generate token** and copy it (it starts with `github_pat_`). GitHub only shows it once, so store it in a password manager.

### 3. Connect the app

1. In the app, open **Sync & backup** (or press **Connect to GitHub** on the Welcome screen).
2. Enter your GitHub username, the repo name (`todo-list-data`) and the token, then press **Connect**.
3. Repeat step 3 on each other device or browser you use. Each one needs the token pasted once.

If you already have tasks on a device, they're merged into your repo the first time you connect.

## Install it as an app

- **iPhone:** open the link in Safari › Share › **Add to Home Screen**. Open the app from the new icon and connect again in **Sync & backup**. The home-screen app keeps its own storage, separate from Safari.
- **Android:** in Chrome, menu › **Install app**.
- **Mac:** in Safari, File › **Add to Dock**. In Chrome or Edge, use the install icon in the address bar.
- **Quick add shortcut:** open `https://christinaw97.github.io/todo-list/#add` to jump straight to adding a task. On iPhone you can put this in a Shortcuts "Open URLs" action and use Siri.

## How your data is handled

- Your tasks are stored on your device, and, if you connect GitHub, in a file called `tracker.json` in your private repo.
- Your token is stored only in your browser (or home-screen app). It is only ever sent to GitHub.
- Every sync is a commit, so your repo keeps a full history you can roll back to.
- A few seconds after a change, and every minute while the app is open, the app pulls the file from GitHub, merges it task by task (the newest edit of each task wins), and saves it back.
- If you edit the same task on two devices within a minute, the later edit is kept.

## Back up your data

If you don't connect GitHub, clearing your browser data erases your tasks. Open **Sync & backup** and press **Download backup (.json)** now and then. To restore, press **Import a backup (.json)**. Importing merges with what's already there and never deletes anything.

Even when GitHub is connected, a downloaded backup is a good second copy.

## If something goes wrong

- **"Sync problem" in the sidebar:** open **Sync & backup** to read the message. An expired token is the most common cause. Make a new one and paste it in.
- **Lost or stolen device:** on GitHub, delete the token (Settings › Developer settings), make a new one, and paste it into your other devices.
- **Tasks missing on a new device:** check that your username, repo name and branch match exactly, and that the token has access to the data repo.
- **App looks out of date:** close and reopen it. It checks for updates when it starts.
- **Leaving this app:** your data is the readable `tracker.json` in your repo, and **Download backup** gives you the same file anytime.

## Want your own copy of the app?

You don't have to. Using the link above with your own data repo is the simplest route, and you'll get updates automatically. If you'd like to change the app itself:

1. Fork this repo (or make a new **public** one and upload `index.html`, `manifest.webmanifest`, `sw.js` and the `icons` folder).
2. Go to **Settings › Pages**, set Source to **Deploy from a branch**, Branch **main**, folder **/ (root)**, and Save. Your app will be at `https://YOUR-USERNAME.github.io/todo-list/`.
3. When you change `index.html`, also change `VERSION` in `sw.js` and `APP_VERSION` in `index.html` (for example `todo-v20` to `todo-v21`) so installed copies pick up the new version. Your data isn't touched.
4. Update the app link in this README, and the "Read the setup guide" link in the Welcome screen, to point at your copy.

## Privacy note

This public repo contains only the app code, and no personal data. Your data lives in your own private repo.
