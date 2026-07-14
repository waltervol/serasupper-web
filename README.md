# serasupper-web

Public website for **SeraSupper** (iOS app by Harper Advanced Technologies).
Static HTML/CSS — no build step, no dependencies. Deployed on **Cloudflare Pages**
at **https://serasupper.com**.

This is the **canonical** source of the published Privacy Policy. The `.docx`
export in the app repo is a convenience copy only — edit the policy *here* first.

## Pages
- `/` — landing placeholder (`index.html`)
- `/privacy/` — Privacy Policy (App Store Connect Privacy Policy URL)
- `/support/` — Support + FAQ (App Store Connect Support URL)
- `404.html`, `robots.txt`, `sitemap.xml`, `favicon.svg`

## Local preview
Serve from the repo root (absolute `/` paths need a server, not `file://`):

```bash
python3 -m http.server 8000
# open http://localhost:8000/  ·  /privacy/  ·  /support/
```

## Deploy (Cloudflare Pages)
1. Push this folder to a new **public** GitHub repo named `serasupper-web`.
2. Cloudflare dashboard → **Workers & Pages → Create → Pages → Connect to Git** →
   pick the repo. Framework preset **None**, no build command, output dir = `/` (root).
3. **Custom domains** → add `serasupper.com` and `www.serasupper.com`
   (set `www` to redirect to the apex). SSL provisions automatically.
4. Every push to the default branch redeploys.

## DNS (one-time)
`serasupper.com` is registered at **Namecheap**. In Namecheap, set the domain’s
**nameservers** to the two Cloudflare provides when you add the site. `serasupper.com`
carries no email, so this does not affect mail — company email stays on
`harpertech.net` at Zoho.

## After deploy
Add these to **App Store Connect**:
- App Information → **Privacy Policy URL**: `https://serasupper.com/privacy`
- TestFlight → Test Information → **Privacy Policy URL**: same
- **Support URL**: `https://serasupper.com/support`

## Contact
support@harpertech.net
