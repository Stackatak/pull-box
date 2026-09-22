# Pullbox: turning it into an Android app

This folder is Pullbox packaged as a progressive web app (PWA). It has everything needed:

- `index.html`: the app itself
- `manifest.webmanifest`: the app's name, colors and icons
- `sw.js`: lets the app open without internet after the first load
- `icons/`: app icons

There are three stages: put it online (free), check it on your phone, then generate the APK.

## Stage 1: Put it online with GitHub Pages (about 5 minutes)

1. Go to https://github.com and create a free account if you don't have one.
2. Click the **+** in the top-right corner, then **New repository**.
3. Name it `pullbox`, set it to **Public**, and click **Create repository**.
   GitHub Pages is only free for public repositories. Anyone with the link could view the site and its code.
4. On the new repository page, click **uploading an existing file**.
5. Unzip this package on your computer. Drag everything *inside* the `pullbox-pwa` folder into the upload box: `index.html`, `manifest.webmanifest`, `sw.js`, `README.md` and the `icons` folder.
   The files must sit at the top level of the repository, not inside a `pullbox-pwa` folder.
6. Click **Commit changes**.
7. Go to **Settings** (top of the repository), then **Pages** in the left sidebar.
8. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose the **main** branch and the **/ (root)** folder, and click **Save**.
9. Wait a minute or two and refresh the page. A link appears at the top, like `https://YOUR-USERNAME.github.io/pullbox/`. That's your app's address.

## Stage 2: Check it on your phone

1. Open your GitHub Pages link in **Chrome** on your Android phone.
2. Tap the **⋮** menu, then **Add to Home screen** (or **Install app**), then **Install**.
3. Pullbox now has its own icon and opens full-screen like an app, without Chrome's address bar.

For your own phone this is often all you need, and it updates automatically whenever you update the website. Continue to Stage 3 if you want an actual APK file.

## Stage 3: Generate the APK with PWABuilder

1. On a computer, go to https://www.pwabuilder.com.
2. Paste your GitHub Pages link into the box and click **Start**.
3. PWABuilder checks the app and shows a report card. Pullbox already includes the manifest, icons and offline support it looks for.
4. Click **Package for stores** (or **Generate Package**), then choose **Android**.
5. In the Android options, keep the defaults. The **Package ID** can be anything unique, like `io.github.yourname.pullbox`.
6. Click **Generate** and download the zip file.
7. Unzip it. Inside you'll find an `.apk` file for installing directly (sideloading) and an `.aab` file, which is only for the Play Store.
   **Keep the signing key file and the signing info text file somewhere safe.** You need them to publish updates to the same app later.

## Stage 4: Install the APK on your phone

1. Send the `.apk` to your phone: email it to yourself, upload it to Google Drive, or copy it over a USB cable.
2. On the phone, tap the `.apk` file to open it.
3. Android asks for permission to install unknown apps. Tap **Settings**, turn on **Allow from this source** for the app you opened it with (Files, Chrome, Drive or Gmail), then go back.
4. Tap **Install**, then **Open**.

The APK is a thin wrapper around your GitHub Pages site, so the site must stay online. When you upload a new `index.html` to GitHub, the app picks up the changes the next time it opens with internet. No new APK is needed.

## Updating Pullbox later

1. In your GitHub repository, click `index.html`, then the pencil or **⋯ → Upload files**, and upload the new version with the same name.
2. Open `sw.js`, click the pencil icon, and change `pullbox-v1` on the first line to `pullbox-v2` (then v3, and so on). This tells phones to refresh their saved offline copy.
3. Commit the changes. Phones update the next time the app opens online.

## Good to know

- **Your data doesn't carry over.** Profiles, balances, inventories, badges and uploaded images are stored per website. The hosted app starts fresh, separate from the copy you've been opening as a file. To move your cases and badges, use **Admin → Export setup** in the old copy and **Import setup** in the new one. Profiles and inventories can't be exported.
- **Phone storage limits still apply.** The app shares about 5 MB of storage for profile pictures, uploaded images and case icons.
- **Admin password:** the password travels with the file, and anyone viewing the public site's code can find it. Change it before sharing the link widely.
- **Play Store:** the APK is fine to install on your own devices. It wouldn't be accepted on the Google Play Store because of the official card images and Pokémon names, and Play's restrictions on simulated gambling.
