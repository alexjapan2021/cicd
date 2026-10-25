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
