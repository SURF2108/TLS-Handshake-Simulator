# TLS 1.2 Handshake Simulator

An interactive, browser-based simulator of the TLS 1.2 handshake (DHE + RSA, AES-128-CBC + HMAC-SHA256).
Single static page: no build step, no dependencies, no backend.

## Deploy on GitHub Pages
1. Create a new repository on GitHub (for example `tls12-handshake-simulator`). Public is simplest; Pages on private repos needs a paid plan.
2. Upload every file in this folder to the **root** of the repo (`index.html`, `404.html`, `.nojekyll`, `README.md`).
   - Web upload: *Add file > Upload files*, drag the files in, then *Commit changes*.
   - Or with Git:

         git init
         git add .
         git commit -m "Add TLS 1.2 simulator"
         git branch -M main
         git remote add origin https://github.com/<your-username>/tls12-handshake-simulator.git
         git push -u origin main

3. In the repo go to **Settings > Pages**. Under *Build and deployment* choose **Source: Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.
4. Wait a minute or two. Your site will be at `https://<your-username>.github.io/tls12-handshake-simulator/` (the exact link also appears at the top of the Pages settings).

## Run locally
Open `index.html` in a modern browser. If crypto features are blocked on `file://`, run `python3 -m http.server 8000` in this folder and visit http://localhost:8000.

## Notes
- Uses the browser Web Crypto API (HMAC, SHA-256, AES-CBC, RSA), which needs HTTPS or localhost. GitHub Pages serves HTTPS automatically.
- Three RSA-2048 keys are generated on first load, so the first render can take a second or two.
- Simplified on purpose: plain-text certificates instead of X.509, small Diffie-Hellman numbers, a derived CBC IV, PKCS#7 padding.
