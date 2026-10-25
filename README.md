# Deploy a simple HTML page with GitHub Actions

This beginner example deploys the files in the repository to GitHub Pages.

## One-time setup

1. Create a GitHub repository and push these files to its `main` branch.
2. In the repository, open **Settings / Pages**.
3. Under **Build and deployment / Source**, select **GitHub Actions**.
4. Open the **Actions** tab and watch **Deploy HTML site to GitHub Pages** run.

When the run succeeds, its summary shows the published site URL. Later pushes to `main` deploy the updated files automatically. You can also start a deployment manually from **Actions / Deploy HTML site to GitHub Pages / Run workflow**.

## The CI/CD steps

1. **Trigger (CI):** a push to `main` starts the workflow. `workflow_dispatch` also lets you start it by hand.
2. **Get files:** `actions/checkout` copies the repository into the runner.
3. **Package:** `actions/upload-pages-artifact` uploads the repository root as a Pages artifact.
4. **Deploy (CD):** `actions/deploy-pages` publishes that artifact to GitHub Pages.

Put `index.html` in the repository root. Other HTML, CSS, JavaScript, and image files there are published too. If your site lives in a folder, change the artifact `path` in `.github/workflows/deploy.yml` to that folder.

## Google sign-in demo

`login.html` is a Google sign-in page built with Firebase Authentication. It starts in setup mode until you connect it to a Firebase project:

1. Create a Firebase project at [Firebase Console](https://console.firebase.google.com/) and register a Web app.
2. In **Authentication / Sign-in method**, enable **Google**.
3. In the web app config shown by Firebase, copy `apiKey`, `authDomain`, `projectId`, and `appId` into `firebaseConfig` in `login.html`.
4. In Firebase Authentication settings, add `alexjapan2021.github.io` to the authorized domains.
5. Push the changes and open `https://alexjapan2021.github.io/cicd/login.html`.

The Firebase web config is intended to be present in browser code. Do not put service account keys or other private credentials in this page. This example signs users in and displays their account; GitHub Pages is static, so protect any private data with a backend or Firebase Security Rules. See [Firebase Google sign-in docs](https://firebase.google.com/docs/auth/web/google-signin).
