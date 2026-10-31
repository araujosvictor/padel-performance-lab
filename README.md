# padel-performance-lab
Padel Performance Lab PILOT PROJECT
# Padel Performance Lab — locally hosted MediaPipe

This version does not import MediaPipe JavaScript, WebAssembly or its model from cross-origin CDNs at runtime. **The GitHub Actions workflow downloads and commits those assets to the repository.** Your visitors' browsers load them from your own GitHub Pages domain.

## Installation

1. Upload `index.html` to the root of your GitHub repository, replacing the old version.
2. Create `.github/workflows/install-assets.yml` in the same repository and paste the included workflow file. GitHub's **Add file → Create new file** accepts the full nested path.
3. In **Settings → Actions → General → Workflow permissions**, choose **Read and write permissions** and save (if your repository allows this setting).
4. In the **Actions** tab, run **Install local pose tracking assets** using **Run workflow**. It may also start automatically after the files are pushed.
5. Wait for the workflow to succeed. Confirm the repository contains `vendor/mediapipe/vision_bundle.mjs`, `vendor/mediapipe/wasm/` and `vendor/mediapipe/pose_landmarker_lite.task`.
6. Ensure **Settings → Pages** is deploying `main` from `/(root)`. Wait for Pages deployment and hard-refresh your website.

If the workflow fails, open its log. It requires GitHub Actions to reach npm and Google Cloud Storage. If the repository's branch protection blocks automatic commits, use a pull request or manually upload the assets.

## Notes

- The `.github` workflow file is hidden on some computers because its folder name starts with a dot. The ZIP contains it.
- You must upload **both** the HTML and workflow; uploading only `index.html` will cause a local-file-missing error.
- Video processing happens in the browser. Model files are downloaded to the browser from your GitHub Pages site; they are not embedded in this ZIP.
- This release was syntax checked, but remote downloads and live browser execution could not be tested in the authoring environment.
