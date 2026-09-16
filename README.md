# tecron-site

The public landing page for **www.tecron.be**: a single static `index.html`, served by
GitHub Pages. No build step, no external fonts or scripts, no cookies.

Legal pages live separately at `legal.tecron.be` (repo `tecron-legal`); this site links to
them.

## DNS at Telenet (cloud.telenet.be)

**Required — the `www` record:**

```
Host / name:  www            (i.e. www.tecron.be)
Type:         CNAME
Value:        eddycornet.github.io
```

**Optional — make `tecron.be` (without www) redirect to www.** Add these on the apex
(host `@` or left blank). GitHub then redirects `tecron.be` → `www.tecron.be` automatically:

```
A     185.199.108.153
A     185.199.109.153
A     185.199.110.153
A     185.199.111.153
AAAA  2606:50c0:8000::153
AAAA  2606:50c0:8001::153
AAAA  2606:50c0:8002::153
AAAA  2606:50c0:8003::153
```

**Do not touch the MX records** — email for `@tecron.be` runs on Google Workspace, and web
records are independent of mail records.

`tecron.be` is already verified in GitHub (done for `legal.tecron.be`), so `www` is covered
without extra verification.

## After DNS propagates (up to a few hours)

```
dig +short www.tecron.be      # → eddycornet.github.io → the Pages IPs
open https://www.tecron.be
```

Then in the repo **Settings → Pages**, tick **Enforce HTTPS** once the certificate is
issued.

## Editing

All content is in `index.html`. The company details in the footer (name, address, VAT
number, contact) are there because a Belgian business website must identify the business —
keep them.
