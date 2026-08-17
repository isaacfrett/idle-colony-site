# idlecolony.app

The site for **Idle Colony**, an iOS idle game. Four static files, no build step,
served by GitHub Pages at [idlecolony.app](https://idlecolony.app).

| File | Why it exists |
|---|---|
| `index.html` | What the game is. |
| `privacy.html` | **Required by Apple** before the first external TestFlight build, not just before release. |
| `support.html` | Also required — App Store Connect will not accept a listing without a support URL. |
| `app-ads.txt` | Authorises the developer's AdMob publisher ID to sell inventory for apps on this domain. Inert until an ad SDK ships, and correct when it does. |
| `CNAME` | `idlecolony.app`, which is what points Pages at the custom domain. |
| `style.css` | Doc 11 §11.2's UI palette, so the site and the game are recognisably one thing. |

## The privacy policy is not boilerplate

It describes **what the app does today**, which is: nothing. No accounts, no
analytics, no advertising, no network requests at all; the colony is a file on the
device.

Advertising, in-app purchases and iCloud sync are all planned, and the policy says
so in advance rather than pretending they are already covered. **Update this page
before any of them ships**, and update the App Store privacy labels to match — a
policy that quietly starts describing collection that already began is worse than
no policy.

One thing is deliberately unresolved and is written as unresolved: the game's
design specifies gameplay analytics but never says where the events would go, while
the same documents say the game has no backend. Until that is settled, no analytics
ships.

## Publishing

Pushing to `main` publishes. For the custom domain, in the repository's
**Settings → Pages**: source `main` / root, then set the custom domain to
`idlecolony.app` and enable **Enforce HTTPS** once the certificate is issued.

DNS, at the registrar, is the usual GitHub Pages pair:

```
A     @      185.199.108.153        ALIAS/ANAME also works
A     @      185.199.109.153
A     @      185.199.110.153
A     @      185.199.111.153
CNAME www    isaacfrett.github.io
```

The apex `A` records are GitHub's published Pages addresses — worth checking
against [GitHub's current
documentation](https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site)
rather than trusting this file, since they have changed before.
