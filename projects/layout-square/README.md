# Layout Square — the drawing had to survive the rest of the job

**Project creator and maintainer: [Tyler Katayama](https://github.com/tylerkat89)**  
**Personal project · AI-assisted development · local release candidate**

I wanted to connect what a job could look like with what it would take to build it. Put the work into a job photo at a measured scale, change the design, and carry those changes into the materials. Then keep track of what was bought, used, and returned.

Getting those pieces to agree became the real project.

## First, give the picture measurements

A photo gives you perspective. A material list needs dimensions.

Layout Square's geometry core uses matrix operations, a linear solver, and homography mapping to connect a measured ground reference to image coordinates. Camera calibration and projection let the design sit in that perspective. The setup still has assumptions: level ground, limited lens distortion, and measurements checked against a tape.

That connection matters because changing a dimension should change the work behind it. A larger slab needs more concrete. A longer beam needs stock that can actually accommodate the cut. Two seven-foot cuts cannot come out of one twelve-foot board just because the total footage looks close.

## Then the two versions stopped agreeing

The photo-design version had the richer editor and material assemblies. The job portal had stronger inventory accounting and pricing records. Replacing either one wholesale would throw away working behavior.

The consolidation kept the design tools and brought their assembly logic into the portal's accounting foundation. Old jobs needed special care: the versions identified material connections differently. Regenerating those connections could disconnect inventory history or create duplicate requirements.

The fix preserves existing connections and prices. New design items get the new assembly starters. Changing the system cannot mean losing the job that was already in it.

## Buying material and using material are different events

This is where a useful-looking total can become a wrong total.

The inventory ledger separates purchase cash from material consumption. It keeps receipt costs, allocates stock in receipt order, and restores the original allocation when material is returned. A later supplier price cannot rewrite the cost of material already used.

Missing prices stay visibly unknown. They do not quietly turn into zero-dollar materials. Purchase quantities account for package sizes and usable stock lengths.

Those rules make the connection from design to cost worth keeping.

## The pricing tests passed, but a runtime detail was missing

The supplier adapter copied the native `fetch` function into an options object and called it as a method. A receiver-sensitive runtime can reject that call. Earlier tests used arrow-function mocks, which did not reproduce the restriction.

The repair calls `globalThis.fetch` through a wrapper. A regression test now substitutes a receiver-sensitive transport and checks that the lookup succeeds.

This reproduced a code defect. A successful mock lookup still does not establish that real credentials, quota, network access, and supplier results will work together in production.

## A saved job has to survive closing the app

The earlier preview stored records in memory. The local edition uses file-backed storage, serialized writes, and revision checks so a restart does not erase inventory and a stale save cannot silently overwrite a newer one.

The Windows package also includes a runtime and launcher. Opening the workspace should not require someone to install development tools first.

There are still two save paths: a full design export includes the photo and design; the local inventory record serves the job picker. Making that distinction easier for another person to understand is part of the remaining work.

## What is verified

The supplied validation report records **24 passing automated suites** across geometry, image processing, assemblies, inventory, pricing, APIs, migration, and persistence.

A focused review on **November 8, 2026** reran the supplied inventory suite (**33 passing checks**), materials suite (**22 passing checks**), receiver-sensitive pricing regression, and local persistence/revision-conflict regression. The persistence check used a writable workspace temporary directory. This was a focused rerun, not a new full application or field validation.

Evidence reviewed: `core.js`, `inventory-core.js`, `materials-core.js`, `supplier-pricing.mjs`, `local-bucket.mjs`, their focused tests, and the supplied appraisal, repair notes, launcher notes, and validation report. This page documents the supplied local package; it does not publish that source package.

## Where it stands

Layout Square is a local release candidate for concept design and job planning. Real-photo field accuracy, live supplier pricing, and a complete pilot workflow still need validation. The consolidated package has not updated the existing hosted portal.

I use AI-assisted workflows to build and investigate. My responsibility is deciding what the tool needs to do, inspecting the results, and keeping the evidence attached to the claims.

This is the work I want my GitHub to show: the problem, the decisions, the failures, and what changed because I kept working on it.

[Back to my profile](../../README.md)
