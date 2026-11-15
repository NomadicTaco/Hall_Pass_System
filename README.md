# Hall Pass

A classroom hall pass app. Runs as a static page on GitHub Pages and syncs across devices with Firebase.

## 1. Firebase (free plan)
1. Go to https://console.firebase.google.com and click **Add project**. Analytics isn't needed.
2. **Build > Authentication > Get started > Email/Password > Enable.** On the **Users** tab, click **Add user** and create the teacher sync account (an email and password you'll remember).
3. **Build > Firestore Database > Create database.** Pick a location and start in **production mode**.
4. Open the **Rules** tab, paste in `firestore.rules`, change `YOUR_TEACHER_EMAIL@example.com` to the email from step 2, and click **Publish**.
5. Click the gear > **Project settings > General > Your apps > Web (</>)**. Register an app and copy the `firebaseConfig` values.
6. In `index.html`, find `FIREBASE_CONFIG` near the top and paste `apiKey`, `authDomain`, `projectId` and `appId` between the quotes.
7. **Authentication > Settings > Authorized domains:** add `YOURNAME.github.io` if it isn't listed.

## 2. GitHub Pages
1. Create a new repository and upload `index.html` (and these other files if you like).
2. **Settings > Pages > Build and deployment > Deploy from a branch > main / (root) > Save.**
3. Your address will be `https://YOURNAME.github.io/REPO/`.

## 3. Each device
Open the address, enter the teacher sync email and password once when asked, then tap **Add to Home Screen**. Then open the page, tap the lock button and set the teacher passcode (the first device only).

The Firebase API key in `index.html` is meant to be public. Access is controlled by the rules in step 1.4.
