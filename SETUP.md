# Firebase setup for team votes

The site writes team votes to Firebase Realtime Database. Team choices and the names associated with votes are publicly readable so the voting section can show who voted for each team. Each guest can only write their own name. A hashed name claim prevents another account from registering the same name (ignoring capitalization and repeated spaces).

1. In Firebase Authentication, enable **Anonymous** sign-in.
2. In **Authentication → Settings → Authorized domains**, add `ebinjosekj.github.io` (the GitHub Pages host).
3. In **Realtime Database → Rules**, paste the contents of `database.rules.json` and click **Publish**.
4. Publish the site over HTTPS with GitHub Pages. Team choices cannot be saved when the page is opened directly from a local `file://` URL.

After changing database rules, publish the updated contents of `database.rules.json` in the Firebase console as well as deploying the website.

The Firebase web configuration in `index.html` identifies the public web app. Database access is enforced by the Realtime Database rules; never put a service-account key in the website.
