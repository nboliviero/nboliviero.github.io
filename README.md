# nboliviero.github.io
Host domain for TeslaFleetAPI

## Setup
### Step 1: Create a Public GitHub Repository
1. Log into your GitHub account.
2. Create a new repository named exactly `yourusername.github.io` (replace `yourusername` with your literal GitHub username).
3. Ensure the repository visibility is set to Public.
4. Check the box to **Add a README file** to initialize the repository structure.
  
### Step 2: Build the Directory Structure and Add the Public Key
Tesla's servers strictly fetch your public key file from a fixed sub-path relative to your domain root.
1. In your repository, click **Add file > Create new file**.
2. In the file path field, type exactly: `.well-known/appspecific/com.tesla.3p.public-key.pem`.
3. Paste the text contents of your public key file (usually beginning with `-----BEGIN PUBLIC KEY-----`) directly into the file editor box.
4. Click **Commit changes...** at the top right to save the file into your repository.
  
### Step 3: Add the Mandatory `.nojekyll` File
By default, GitHub Pages uses a build tool called Jekyll, which automatically hides any directory beginning with a dot (like `.well-known`).
1. Go back to the main root folder of your repository.
2. Click **Add file > Create new file**.
3. Name this file exactly `.nojekyll`. Leave the contents completely empty.
4. Click **Commit changes...** to save.

### Step 4: Turn on GitHub Pages
1. Navigate to your repository's **Settings** tab.
2. Scroll down to the left sidebar menu and click **Pages**.
3. Under the **Build and deployment** section, verify that the source drop-down menu is set to **Deploy from a branch**.
4. Set your primary branch (usually `main` or `master`) as the deployment source and click **Save**.
5. Give GitHub 1 to 2 minutes to build your static page.

### Step 5: Verify the Deployment and Link to Tesla
Before pasting your domain into the [Tesla Developer Portal](https://developer.tesla.com/), verify it responds properly.
1. Open your web browser and test your public endpoint URL:
   `https://yourusername.github.io/.well-known/appspecific/com.tesla.3p.public-key.pem`
2. If your browser successfully downloads or prints the raw public key text, your hosting is complete. If you encounter a 404 error, double-check that your repo root contains the .nojekyll file.
3. Copy your base hosting domain (`https://yourusername.github.io`) and paste it into the Allowed Origins field inside your Tesla Developer Application console.
