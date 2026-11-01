# Site in development — specification

This document is **generated from the graph** by `tl docs`; `tl docs --check` gates it
in CI. The prose headings are hand-owned — everything between `tl:*` markers is injected
from the YAML items, so this document can never drift from the graph.

It carries
<!-- tl:count type == 'requirement' -->
15
<!-- tl:end --> requirements.

## Purpose

<!-- tl:item INT-0001 -->
**INT-0001 — A site that is public while it is being built is judged by what it serves today** — `intent`, status `ratified`

> A site under active development is often reachable before it is finished. Visitors, crawlers and other sites do not wait for the finish. They judge the site by the response they get now. So the quality of a site in development is the quality of its worst reachable response, not the quality of the plan. Every published address is a promise. The site keeps every promise it has made, or says plainly at that address that it cannot yet.

**origin**: hybrid · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:8db66db4b669c467c4c0be701df2b2866a27bfd8e2286c26ff69d9ac03873193
<!-- tl:end -->

## What goes wrong

The requirements below exist to mitigate three risks. Each risk names something that
has happened to a real site; none of them is hypothetical.

<!-- tl:item RISK-0001 -->
**RISK-0001 — A promised destination that fails reads as abandonment** — `risk`, status `ratified`

> A link is published before its destination exists, and the destination answers with an error. A visitor cannot tell not-yet from gone. A crawler records the failure. The site's credibility is spent at the first click, and the cost lands on the whole site, not on the missing page.

**origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:c501cc7b6c74aeb4575331abf77f3defea046c5d4a9e3f53d83debd001b044a5
<!-- tl:end -->

<!-- tl:item RISK-0002 -->
**RISK-0002 — Placeholder content outlives its replacement** — `risk`, status `ratified`

> Interim content is indexed, cached, linked and archived like any other content. Once it is in the record it can outlive the real content that replaces it. Sample text, draft wording and holding pages that were never meant to be seen are then quoted back at the site for years.

**origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:792acb19864a5066eba57e4d9a09bb2560699b73325b11745e55a81dea7ee968
<!-- tl:end -->

<!-- tl:item RISK-0003 -->
**RISK-0003 — An interim arrangement becomes permanent because nothing removes it** — `risk`, status `ratified`

> A holding page, a temporary redirect or a hand-applied fix is put in place to get past a moment. Nothing records that it is interim or what would end it. The moment passes, the people change, and the arrangement stays. The site accumulates exceptions nobody can explain.

**origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:2f6a15511eb9fd0728b2698325acd26a279ba5c24d86c170839797958780e338
<!-- tl:end -->

## Requirements

<!-- tl:table type == 'requirement' -->
| UID | Type | Status | Title |
|---|---|---|---|
| REQ-0001 | requirement | ratified | A link is published only when its destination answers |
| REQ-0002 | requirement | ratified | A holding page says what is coming and that it is not here yet |
| REQ-0003 | requirement | ratified | A holding page is a successful response |
| REQ-0004 | requirement | ratified | A holding page is kept out of search indexes |
| REQ-0005 | requirement | ratified | A holding page carries the finished site's security posture |
| REQ-0006 | requirement | ratified | A holding page sets no cookies, keeps no state and accepts no input |
| REQ-0007 | requirement | ratified | A holding page loads nothing from a third party |
| REQ-0008 | requirement | ratified | A holding page is a real page for every visitor |
| REQ-0009 | requirement | ratified | Every holding page has a recorded owner and removal condition |
| REQ-0010 | requirement | ratified | Every published link is walked by an automated check |
| REQ-0011 | requirement | ratified | A published address is never abandoned |
| REQ-0012 | requirement | ratified | No sample or draft text reaches a public response |
| REQ-0013 | requirement | ratified | Interim content ships through the same delivery path as finished content |
| REQ-0014 | requirement | ratified | Every public response is verified from the visitor's position |
| REQ-0015 | requirement | ratified | The site says what is live and what is still to come |
<!-- tl:end -->

### Promises

<!-- tl:item REQ-0001 -->
**REQ-0001 — A link is published only when its destination answers** — `requirement`, status `ratified`

> A site publishes a link to a destination only when that destination returns a successful response. Until then the link is either not published or points at a holding page that answers. A published link that leads to an error is a defect in the site that published it, whoever owns the destination.

*Rationale:* Rejected: publishing the link early to reserve the name. The name is reserved by owning the domain, not by linking to it. Who pays: the site owner, who must stand up a holding page before announcing anything. That is a small one-off cost; a dead link costs every visitor.

*Implements:* INT-0001
*Mitigates:* RISK-0001

**priority**: must · **origin**: hybrid · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:4fb8bd38351b753b0aadbe94033cbcd2222ae2fc540e90dc751144759c7ec120
<!-- tl:end -->

<!-- tl:item REQ-0011 -->
**REQ-0011 — A published address is never abandoned** — `requirement`, status `ratified`

> During active development addresses move often. When content moves, the old address redirects permanently to the new one. When content is withdrawn, the old address returns 410 with a page that says the content has gone and where to go instead. An address that once answered does not start returning 404.

*Rationale:* Rejected: leaving old addresses to 404 because nobody has linked to them yet. The site cannot know who has linked to them. Who pays: the developer, who keeps a redirect list. It is a few lines per move.

*Implements:* INT-0001
*Mitigates:* RISK-0002

**priority**: should · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:c33d0c16ba06fe7f8dfa8481f997341bab9b5a556d0906bffaff145e52ecca6c
<!-- tl:end -->

<!-- tl:item REQ-0015 -->
**REQ-0015 — The site says what is live and what is still to come** — `requirement`, status `ratified`

> A site in development states its own status somewhere a visitor will find it: which parts are live, which are coming, and where to report a problem. This may be one page or a line on each holding page. It is kept current by the same changes that ship content, not by a separate editorial effort.

*Rationale:* Who pays: the site owner, who admits in public that the site is unfinished. That is cheaper than a visitor discovering it alone.

*Implements:* INT-0001
*Mitigates:* RISK-0001

**priority**: should · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:51910f4107997bce8f76a670301a7b92a556f1b182d6f2959c371faa54ac0edc
<!-- tl:end -->

### The holding page

<!-- tl:item REQ-0002 -->
**REQ-0002 — A holding page says what is coming and that it is not here yet** — `requirement`, status `ratified`

> A holding page names what the address is for, states plainly that the content is not yet available, and links back to the site that sent the visitor there. It does not pretend to be the finished thing. Where a date or a condition can be given honestly it gives one. Where it cannot, it says nothing about timing rather than guessing.

*Rationale:* Rejected: a bare coming-soon line with no context. The visitor followed a link that described the destination, so the holding page must at least repeat that description. Otherwise the click was wasted.

*Implements:* INT-0001
*Mitigates:* RISK-0001

**priority**: must · **origin**: hybrid · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:66af9a10eae1cf553c515721f4534fa18355860c24f3af9ffac19e8937d4002e
<!-- tl:end -->

<!-- tl:item REQ-0003 -->
**REQ-0003 — A holding page is a successful response** — `requirement`, status `ratified`

> A holding page returns HTTP 200 at the address that was published. It is a successful response whose content says not yet. It does not return 404, 503 or any other error status at that address. Addresses under a holding host that were never published still return 404, with the holding page as the body where that helps.

*Rationale:* Rejected: 503 with Retry-After. That status describes an outage, not an absence. Crawlers treat a long-lived 503 as a failing site and eventually drop the address, and many edge networks replace a 5xx body with their own error page, so the visitor never sees the site's wording. Rejected: 404. It is the same response a mistyped address gives, so it says nothing.

*Implements:* INT-0001
*Mitigates:* RISK-0001

**priority**: must · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:f2bc6bea88c34e7d5a81455f0a9023d11a6776d3af5e6768e19c4f76a7dbdb3d
<!-- tl:end -->

<!-- tl:item REQ-0004 -->
**REQ-0004 — A holding page is kept out of search indexes** — `requirement`, status `ratified`

> A holding page declares itself not indexable in both the response header and the document, and it is not listed in any sitemap the site publishes. When the real content ships, the noindex marking leaves with the holding page. The address is never blocked in robots rules, because a blocked address cannot be re-read when the real content arrives.

*Rationale:* Rejected: a robots.txt disallow. It stops the crawler reading the page but not from listing the address, and it has to be undone later by hand. A noindex marking on the page removes itself with the page.

*Implements:* INT-0001
*Mitigates:* RISK-0002

**priority**: must · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:053d301a9397db937329ff829653053ac85ba7c5a10b86394cccd11d42f1f23e
<!-- tl:end -->

<!-- tl:item REQ-0005 -->
**REQ-0005 — A holding page carries the finished site's security posture** — `requirement`, status `ratified`

> A holding page is served over the same TLS and with the same security headers as the finished site will be. Its content security policy is the narrowest the page can carry. A holding page runs no script, so its policy allows none. It is not a place to relax anything because it is only a placeholder.

*Rationale:* The holding page is the first thing served at that origin. Browsers, crawlers and preload lists record what they see, and a weak start is remembered. Who pays: the site owner, once, in setting the headers before the first byte is served.

*Implements:* INT-0001

**priority**: must · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:ae59b08b627ea177eb0c9d73b6408bd3c96ddf439daad6ac88b0c47f2a7687ba
<!-- tl:end -->

<!-- tl:item REQ-0006 -->
**REQ-0006 — A holding page sets no cookies, keeps no state and accepts no input** — `requirement`, status `ratified`

> A holding page sets no cookie, stores nothing in the browser and contains no form or other input. It is a read-only statement. Where the address is reserved for a stricter trust boundary than the site that links to it, such as an authentication origin, the holding page contains nothing that boundary would later have to disown.

*Rationale:* Anything a holding page collects has no owner and no purpose yet. Anything it stores becomes state the real content inherits. Rejected: an email sign-up on the holding page. That is a landing page, which NG-0001 excludes.

*Implements:* INT-0001

**priority**: must · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:35b9eefed220531b2b401c66f0cd8196bfa92fedd50c793c991ce306a5df1242
<!-- tl:end -->

<!-- tl:item REQ-0007 -->
**REQ-0007 — A holding page loads nothing from a third party** — `requirement`, status `ratified`

> A holding page references no third-party resource: no external font, script, stylesheet, image or analytics. Everything it needs is served from its own origin or inlined. It can therefore load with no network access beyond its own host, and it tells no one else that the visitor came.

*Rationale:* Who pays: the page's author, who gives up a web font and a visitor counter. The page exists for minutes of a visitor's time across its whole life. A third-party request costs privacy and a dependency for nothing.

*Implements:* INT-0001

**priority**: should · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:019f4063a8905d1a60023568f60d92b6001738ae5a6db2a615041fffb501d7a4
<!-- tl:end -->

<!-- tl:item REQ-0008 -->
**REQ-0008 — A holding page is a real page for every visitor** — `requirement`, status `ratified`

> A holding page has a page title that names the site, a declared language, a heading, readable contrast and link text that says where each link goes. It reads correctly with styles disabled and with a screen reader. It is text, not an image of text.

*Rationale:* A holding page is often the only page many visitors ever see. It must meet the same accessibility bar as the finished site, and it is small enough that there is no excuse for missing it.

*Implements:* INT-0001

**priority**: must · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:3fdd8e1be232a5b11e084f501855415c0f13b8e8002edc7f0aa5a20e76f91822
<!-- tl:end -->

<!-- tl:item REQ-0009 -->
**REQ-0009 — Every holding page has a recorded owner and removal condition** — `requirement`, status `ratified`

> For each holding page the site records, where its requirements live, who owns it and what event ends it. The holding page is removed by the same change that ships the content it stood in for, never by a later clean-up. A holding page nobody can name the owner of is a defect.

*Rationale:* Rejected: a temporary label alone. Labels do not remove anything. The removal condition ties the page to a change someone will make anyway.

*Implements:* INT-0001
*Mitigates:* RISK-0003

**priority**: must · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:bffc0c13e4447c71960e0a3993e79f3f0041a74ee22904ee93ab837673c7aa89
<!-- tl:end -->

### Keeping it true

<!-- tl:item REQ-0010 -->
**REQ-0010 — Every published link is walked by an automated check** — `requirement`, status `ratified`

> An automated check follows every link the site publishes, from outside the site, and fails on any response that is not successful. It runs after every deployment and on a schedule, because a destination the site does not own can fail without any change to the site. A failing check is treated as a defect, not as noise.

*Rationale:* Rejected: checking only at deploy time. Links point at other people's sites, and those change on their own clock. Who pays: whoever runs the site's pipeline, in one more job. The alternative is finding out from a visitor.

*Implements:* INT-0001
*Mitigates:* RISK-0001

**priority**: must · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:7347fb84674d3345454d71ac1ebc20aac9b0f52c5fd8ae9a6ba571cfecd2e1b4
<!-- tl:end -->

<!-- tl:item REQ-0012 -->
**REQ-0012 — No sample or draft text reaches a public response** — `requirement`, status `ratified`

> Placeholder text, sample data, lorem ipsum, editorial notes and to-do markers do not appear in any public response. A page that is not ready to be read is not published; a holding page stands in its place. An automated check for known placeholder patterns runs before each deployment.

*Rationale:* Rejected: relying on review to catch it. Placeholder text looks like content to a tired reviewer, and a pattern check does not tire. Who pays: the author, who must decide a page is finished before it is public. That is the point.

*Implements:* INT-0001
*Mitigates:* RISK-0002

**priority**: must · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:cf869e3dfa6da2b142f7ebd5a6b4c25c0c71c7fd27bda2a4f0856c85b6a5b7ca
<!-- tl:end -->

<!-- tl:item REQ-0013 -->
**REQ-0013 — Interim content ships through the same delivery path as finished content** — `requirement`, status `ratified`

> A holding page, a redirect or any other interim response is built, reviewed and deployed through the same pipeline as the finished site. Nothing is edited on a live server by hand. What is running is always what is committed, so an interim response can be found, understood and removed later by reading the repository.

*Rationale:* Rejected: uploading the file by hand because it is only a static page. A hand-placed file is exactly the interim arrangement RISK-0003 describes. Nothing records it and nothing removes it.

*Implements:* INT-0001
*Mitigates:* RISK-0003

**priority**: must · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:41374ff0de53c291951eb1e6c7203ddc5de5cf3a08554d9fd4db8983195e5b39
<!-- tl:end -->

<!-- tl:item REQ-0014 -->
**REQ-0014 — Every public response is verified from the visitor's position** — `requirement`, status `ratified`

> After each deployment the site is checked from outside its own infrastructure, at its public addresses, through whatever edge or proxy sits in front of it. The check confirms the status code, the headers the site claims to send, and that the body is the site's own. A check inside the infrastructure does not count, because it does not see what the visitor sees.

*Rationale:* An edge network can rewrite a status, replace a body or strip a header, and the origin never knows. Who pays: the site's pipeline, with one external request per address. The alternative is a green build and a broken site.

*Implements:* INT-0001
*Mitigates:* RISK-0001

**priority**: must · **origin**: ai · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:691734b16bac2cd933f3c4ed81dab23ea05c3879f13acfeb66c4bec2404d8480
<!-- tl:end -->

## Out of scope

<!-- tl:item NG-0001 -->
**NG-0001 — A holding page is not a landing page** — `non_goal`, status `ratified`

> This source does not cover launch marketing. It says nothing about email capture, countdowns, teasers or campaign pages. A holding page tells the truth about an address. A landing page persuades. The two have different owners and different rules.

**origin**: hybrid · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:b0fe28b14bf18fcd8e4fc4e333423b0ac8287fa89df18859f3d60e4ed1102fd8
<!-- tl:end -->

<!-- tl:item NG-0002 -->
**NG-0002 — Planned downtime of a finished site is out of scope** — `non_goal`, status `ratified`

> This source does not cover maintenance windows or outages of content that has already shipped. Those are short, use 503 with Retry-After, and belong to the site's operational runbook. A holding page is for content that has not yet existed at an address.

**origin**: hybrid · **ratified_by**: Henry Grech-Cini · **ratified_fingerprint**: sha256:f53155ba74ce6c5b8d7e95d32336f93670bfc08f8b0ae46731f5452718df23ba
<!-- tl:end -->
