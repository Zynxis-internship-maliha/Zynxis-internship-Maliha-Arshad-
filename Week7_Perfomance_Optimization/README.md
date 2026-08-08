ZYNXIS Frontend Internship — Week 7: Performance & Web Vitals


This repository contains the Week 7 deliverables: the Lighthouse Audit Report template and the documentation needed to reproduce a real performance audit of the application.

Status: the application source from Weeks 1–6 is not present in this project. Only the documentation deliverable has been produced. Every performance number in the report is deliberately left as "Pending measurement" — no Lighthouse run has been executed, and no figure in this repository may be estimated or invented.

Deliverables
Deliverable	Location	Status
Lighthouse Audit Report (PDF)	ZYNXIS_Week7_Lighthouse_Audit_Report.pdf (downloaded artifact)	Template, ready to fill
Optimized source code	—	Not produced; the existing app is not in this project
Project overview
Fill in once the audit target is decided:

Application purpose:
Framework / runtime:
Routing:
Styling system:
State management:
Data layer / APIs:
Deployment target:
Technologies used
This documentation project itself is a TanStack Start + React + Tailwind CSS template. Record the technologies of the audited application here instead, once it is added.

Performance problems discovered
None recorded yet. Populate this section from the baseline Lighthouse run's Opportunities and Diagnostics lists, one row per real finding:

#	Lighthouse finding	Measured cost	Metric affected	Root cause
1				
Optimizations implemented
None yet. As each optimization lands, record it here with the metric it targets:

Image optimization (modern formats, responsive sources, reserved dimensions)
Image lazy loading (loading="lazy" + decoding="async" below the fold; the LCP image stays eager with fetchpriority="high")
Component lazy loading (dynamic import() behind React.lazy + Suspense, with size-matched skeleton fallbacks and error boundaries)
Route- and component-level code splitting; dependency pruning
CLS stabilisation (reserved media space, font-display swap)
Data-layer fixes (deduplicated requests, parallelised fetches, cached queries)
How to run the project
bun install
bun run dev
The dev server is for development only — never audit it with Lighthouse. Unminified code and HMR tooling understate the score by a wide margin.

How to create a production build
bun run build
Then serve the build output over a static server and audit that URL.

How to run Lighthouse
Chrome DevTools
Open the production URL in an incognito window with all extensions disabled.
DevTools > Lighthouse panel > select Performance, Accessibility, Best Practices, SEO.
Choose the Mobile preset with simulated throttling for the headline number; repeat with Desktop.
Click Analyse page load. Run three times and report the median.
Export each run as JSON and HTML and store them next to the report.
Command line
npx lighthouse <production-url> \
  --only-categories=performance,accessibility,best-practices,seo \
  --form-factor=mobile --screenEmulation.mobile \
  --output=json --output=html --output-path=./audits/baseline
Re-run with --output-path=./audits/final after the optimization work.

How to reproduce the performance audit
Capture the baseline against the production build, before any optimization commit.
Record the exact conditions: URL, build type, device preset, throttling, Lighthouse version, browser version, date.
Apply the optimizations.
Re-run under identical conditions. A comparison across different devices, networks or build types is not valid evidence.
Report the median of three runs, not a single best-case run.
Before / after results
Metric	Before	After	Improvement
Performance score	Pending measurement	Pending measurement	Pending measurement
First Contentful Paint	Pending measurement	Pending measurement	Pending measurement
Largest Contentful Paint	Pending measurement	Pending measurement	Pending measurement
Cumulative Layout Shift	Pending measurement	Pending measurement	Pending measurement
Total Blocking Time	Pending measurement	Pending measurement	Pending measurement
Speed Index	Pending measurement	Pending measurement	Pending measurement
Initial JS transferred	Pending measurement	Pending measurement	Pending measurement
Target: Performance, Accessibility, Best Practices and SEO all at 90 or above.

Known limitations
The Week 1–6 application is not present in this project, so no code was audited, optimized, or measured.
All metrics in the report and in the table above are placeholders pending a real Lighthouse run.
Lab scores do not capture real device and network variance; field Core Web Vitals should be tracked separately once the app is deployed.
