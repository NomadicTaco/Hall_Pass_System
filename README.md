# Hall Pass (school edition)

A hall pass app for a whole school. Each teacher signs in with their own account and has their own
rosters, periods, limits and log. An admin account (the principal) adds teachers and can see which
students are out of class across the school. Runs on GitHub Pages and stores data in Firebase.

## 1. Firebase (free plan is plenty for one school)
1. Go to https://console.firebase.google.com and click **Add project**. Analytics isn't needed.
2. **Build > Authentication > Get started > Email/Password > Enable.** Leave **Enable create (sign-up)** turned on; the admin uses it to create teacher accounts.
3. **Build > Firestore Database > Create database.** Pick a location and start in **production mode**.
4. Open Firestore's **Rules** tab, delete everything, paste in `firestore.rules`, and click **Publish**. (There is nothing to edit in the rules.)
5. Click the gear > **Project settings > General > Your apps > Web (</>)**. Register an app and copy the `firebaseConfig` values.
6. Open `config.js` and paste `apiKey`, `authDomain`, `projectId` and `appId` between the quotes.
7. **Authentication > Settings > Authorized domains:** add `YOURNAME.github.io` if it isn't listed.

## 2. GitHub Pages
1. Create a repository and upload `index.html`, `config.js`, `manifest.json` and the three `.png` icons.
2. **Settings > Pages > Build and deployment > Deploy from a branch > main / (root) > Save.**
3. Your address will be `https://YOURNAME.github.io/REPO/`.

## 3. First use
1. **The principal opens the address first** and fills in "Set up your school" (school name, name, email, password). This creates the admin account. Do this right away: until the school exists, the first person to finish this screen becomes the admin.
2. In the admin's **Teachers** tab, add each teacher (name, email, temporary password) and give them those details.
3. Each teacher opens the address on their own tablet, signs in, then taps the lock button to set their own classroom passcode, and enters their roster and period times in **Settings**.

## Who sees what
- **Students:** only the Sign Out screen on the teacher's tablet.
- **Teachers (after the classroom passcode):** their own Sign Out, Log, Passes and Settings, plus **Out of class**, which lists every student out of class across the school.
- **Admin:** **Out of class** and **Teachers** only. Admins don't have a roster.

The Firebase API key in `config.js` is meant to be public. Access is controlled by the rules in step 1.4.
Removing a teacher in the Teachers tab ends their access. Their saved data stays in Firebase.
