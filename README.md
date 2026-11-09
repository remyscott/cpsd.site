# cpsd.site

The root page does two jobs:

- A plain visit to any path redirects to the same path on https://www.cpsd.us.
- A visit that carries `?p=/some/path` (how the Empires server sends people who open empires.cpsd.site directly) shows
  https://empires.cpsd.site/some/path in a full-window iframe, so the address bar reads cpsd.site. The page then drops
  the query from the address, remembers the game's location in sessionStorage (the game reports moves with
  postMessage) and comes back to it on reload. A new tab with no memory goes to cpsd.us as usual.

The tab carries cpsd.us's title and favicon (linked from their site, so it follows theirs), and switching away from the
tab and back to it sends the tab to cpsd.us; the remembered location still brings the next visit back to the game.

Recursion is prevented twice: the Empires server redirects only top-level navigations (Sec-Fetch-Dest: document), not
loads inside a frame, and this page, if it is ever framed, opens the game directly instead of itself.

The Empires service needs `HOSTS={"empires.cpsd.site":{"frame":"https://cpsd.site/"}}` in its environment.

`404.html` is the plain redirect, so unknown paths redirect too. Served by GitHub Pages.

## DNS (at the registrar for cpsd.site)

| Name    | Type  | Value                                                                    |
|---------|-------|--------------------------------------------------------------------------|
| @       | A     | 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153       |
| www     | CNAME | remyscott.github.io                                                      |
| empires | CNAME | the Render host of EmpVC2 (something.onrender.com), added as a custom domain in Render |

GitHub Pages: Settings → Pages → source `main` / root, custom domain `cpsd.site`, enforce HTTPS once the certificate is issued.
