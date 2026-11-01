# Carolin Hartung — Quarto academic website

This is an editable, **multi-page Quarto project** created from the public content at <https://carolin-hartung.de/> (reviewed **1 November 2026**). It is designed for GitHub Pages using the domain already registered at INWX.

## What's included

- `index.qmd` — homepage, academic background, research summary, publication highlight, outreach and contact
- `research.qmd` — research interests, supervisor, current preprint
- `publications.qmd` — publication and arXiv link
- `talks.qmd` — all five talks shown on the source website
- `outreach.qmd` — equality / outreach work and student representation
- `cv.qmd` — short academic CV and the existing Dropbox PDF link
- `_quarto.yml` — navigation, site address, SEO descriptions and sitemap support
- `styles.css` — simple, responsive design; no external fonts or tracking scripts
- `CNAME.template.txt` — contains your domain, but is intentionally **not activated yet**, so you can test GitHub Pages before changing your live website

## Before publishing

**Please review the content** for accuracy and any recent changes, especially PhD status, talk titles, CV and representation roles. The public website described Carolin as a first-year PhD student, but the new site says only "PhD student" to avoid becoming dated.

**Not copied automatically:** The source website displays a photo taken at a blackboard. A stable local copy could not be retrieved in this environment. To add your photo, save it locally as `images/profile.jpg`, then add `![Carolin Hartung at a blackboard](images/profile.jpg)` to `index.qmd` where you want it displayed. The full PDF CV remains on Dropbox, linked from `cv.qmd` (the PDF itself was not downloaded). No teaching history, degree dates, ORCID, office or other unstated claims were invented.

The original source website is hosted with Notion. **Do not change your INWX DNS until the new GitHub Pages version is working at its GitHub URL and you have reviewed the content.** Changing DNS will replace the current website served at the custom domain.

## 1. Install tools and preview locally

Install Quarto (<https://quarto.org/docs/get-started/>) and Git (<https://git-scm.com/downloads>) if needed. Open a terminal inside this folder:

```bash
quarto preview
```

Quarto will display the site in your browser and refresh as you edit the `.qmd` files. Review every page.

## 2. Create your GitHub repository

Create a **public** empty repository named `USERNAME.github.io`, substituting your GitHub username. Then run:

```bash
git init
git branch -M main
git add .
git commit -m "Create Carolin Hartung's academic website"
git remote add origin https://github.com/USERNAME/USERNAME.github.io.git
git push -u origin main
```

If you already have a Git repository, adapt these commands instead of reinitializing it. GitHub may ask you to authenticate using a browser, personal access token or Git credential helper.

## 3. Publish to GitHub Pages

```bash
quarto publish gh-pages
```

Follow the prompts. Under **GitHub repository → Settings → Pages → Build and deployment**, choose **Deploy from a branch**, branch **gh-pages**, folder **/(root)**. For `USERNAME.github.io` repositories, this adjustment is usually needed after the first publish. Check `https://USERNAME.github.io` before switching your domain.

The project intentionally has **no active `CNAME` file yet**, so GitHub Pages can initially be tested at the GitHub URL without redirecting visitors to your existing Notion website.

## 4. Connect your INWX domain

After confirming your site works at `https://USERNAME.github.io`, create the active `CNAME` file (it must have **no extension**) from `CNAME.template.txt`:

```bash
cp CNAME.template.txt CNAME  # macOS/Linux; on Windows copy or rename in File Explorer
quarto publish gh-pages
```

If Quarto asks about uncommitted changes, you can also run `git add CNAME && git commit -m "Set custom domain" && git push` before publishing. Quarto recognizes the `CNAME` file as a website resource and includes it in the published output.

Once the new site is correct, confirm `carolin-hartung.de` under **GitHub → Repository → Settings → Pages → Custom domain**. GitHub also recommends verifying your domain's ownership under your GitHub account Pages settings.

If your domain uses INWX nameservers, sign in at <https://www.inwx.com/> and open **Nameserver → select carolin-hartung.de → DNS entries**. For the root domain, INWX expects the **Name field to be left blank** rather than `@`.

| Name field | Type | Value |
|---|---|---|
| *(blank)* | A | `185.199.108.153` |
| *(blank)* | A | `185.199.109.153` |
| *(blank)* | A | `185.199.110.153` |
| *(blank)* | A | `185.199.111.153` |
| `www` | CNAME | `USERNAME.github.io` |

Replace USERNAME. Existing A/AAAA/ALIAS records that point the same hostnames to the old website may conflict, so review them and replace only those associated with web hosting. **Don't remove email MX / TXT records, other subdomains, or change your nameservers without checking.** If you use another DNS provider's nameservers, make DNS edits there instead.

Allow time for DNS propagation, then enable **Enforce HTTPS** under GitHub Pages settings.

## 5. Google indexing

`website: site-url` is set in `_quarto.yml` to `https://carolin-hartung.de`; Quarto generates `sitemap.xml` when the website is rendered. After publication, verify your domain in [Google Search Console](https://search.google.com/search-console/), submit `https://carolin-hartung.de/sitemap.xml`, and request indexing for the homepage. Indexing and search rankings are not guaranteed.

## 6. Update the website

```bash
git add .
git commit -m "Update website"
git push
quarto publish gh-pages
```

## Reference documentation

- Content source: <https://carolin-hartung.de/>
- Quarto / GitHub Pages: <https://quarto.org/docs/publishing/github-pages.html>
- Quarto site resources: <https://quarto.org/docs/websites/website-tools.html>
- GitHub custom domains: <https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site>
- INWX DNS guide: <https://kb.inwx.com/en-us/3-nameserver/108-how-can-i-forward-a-domain-to-an-ip-address-a-aaaa-record>
