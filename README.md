# cpsd.site

Redirects every path on cpsd.site to the same path on https://www.cpsd.us.
Served by GitHub Pages; `404.html` is the same page so unknown paths redirect too.

## DNS (at the registrar for cpsd.site)

| Name    | Type  | Value                                                                    |
|---------|-------|--------------------------------------------------------------------------|
| @       | A     | 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153       |
| www     | CNAME | remyscott.github.io                                                      |
| empires | CNAME | the Render host of EmpVC2 (something.onrender.com), added as a custom domain in Render |

GitHub Pages: Settings → Pages → source `main` / root, custom domain `cpsd.site`, enforce HTTPS once the certificate is issued.
