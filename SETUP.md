# Firebase setup for team votes

The site writes team votes to Firebase Realtime Database. Public vote data contains only the team choice. Guest names are stored separately so each guest can read only their own name. A private hashed name claim prevents another account from registering the same name (ignoring capitalization, punctuation, and spacing).

1. In Firebase Authentication, enable **Anonymous** sign-in.
2. In **Authentication → Settings → Authorized domains**, add `ebinjosekj.github.io` (the GitHub Pages host).
3. In **Realtime Database → Rules**, paste the contents of `database.rules.json` and click **Publish**.
4. Publish the site over HTTPS with GitHub Pages. Team choices cannot be saved when the page is opened directly from a local `file://` URL.
5. Re-publish the updated `database.rules.json` rules. Existing votes created before name claims were added need claims backfilled in Firebase if those names must be reserved too.

After changing database rules, publish the updated contents of `database.rules.json` in the Firebase console as well as deploying the website.

The Firebase web configuration in `index.html` identifies the public web app. Database access is enforced by the Realtime Database rules; never put a service-account key in the website.
