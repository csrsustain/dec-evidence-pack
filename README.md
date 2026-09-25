# DEC Evidence Pack – CSR Sustain

Digital, sealed DEC client forms (energy data, opening hours, data validation) with e-signing.
No server, no database: pack data travels inside the link, and the signed PDF is created on the client's device.

## Files

| File | Who uses it | Purpose |
|---|---|---|
| `index.html` | Clients | Opens a pack from its link, checks the seal, collects opening hours and signature, produces the signed PDF |
| `prepare.html` | CSR Sustain staff | Enter site data, create sealed client links |
| `public-key.json` | Created by you (see below) | Lets the client page check the seal |

## First-time setup

1. Create a repository (for example `dec-evidence-pack`) and upload `index.html`, `prepare.html` and this README.
2. Settings → Pages → deploy from the `main` branch, root folder. Wait for the site address, e.g. `https://<account>.github.io/dec-evidence-pack/`.
3. Open `…/prepare.html` in Chrome, Edge or Safari. Click **Create seal key**. A key backup file downloads – store it somewhere private (not in GitHub).
4. Click **Download public-key.json** and upload that file to the repository root.
5. Wait a minute and reload `prepare.html`. The seal status should read "Seal key ready and matches the website".

## Everyday use

1. Open `prepare.html`, enter the site details and monthly figures, and click **Create client link**.
2. Click **Copy link** (or **Copy suggested email text**) and paste into your own email to the client.
3. The client opens the link, checks the data, adds opening hours, signs and downloads the PDF.
4. The client emails the PDF back. Check the seal code on the PDF matches the one shown in **Recent packs**.

## Keys

- The **key backup** is the private key. Anyone with it can create valid links, so keep it private. To use another computer or give a colleague access, import it with **Import key backup** on `prepare.html`.
- If the backup is lost, create a new key and upload the new `public-key.json`. Links issued with the old key will stop opening.
- Never upload the key backup file to GitHub.

## Updating the pages

Increase the `build-version` meta tag (pattern `YYYY-MM-DD-NN`) in each edited file on every deployment.

## Limits

- Signed time comes from the signer's device clock; no IP address is recorded.
- Nothing is stored online. Signed forms exist only as the PDF the client sends back.
- "Recent packs" is stored in the preparing browser only.
