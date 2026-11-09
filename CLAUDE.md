# Claude SEO: Universal SEO Analysis Skill

## Project Overview

This repository contains **Claude SEO**, a comprehensive SEO analysis skill for Claude. It follows the Agent Skills open standard and a 3-layer architecture (directive, orchestration, execution). 26 sub-skills, 19 sub-agents, and a knowledge reference system cover technical SEO, content quality, schema markup, image optimization, sitemap architecture, AI search optimization (GEO), local SEO (GBP, citations, reviews, map pack), maps intelligence, semantic topic clustering, search experience optimization (SXO), SEO drift monitoring, e-commerce SEO, and international SEO.

## Architecture

```
claude-seo/
  SKILL.md                           # Main entry point & skill manifest (Claude.ai Custom Skill)
  CLAUDE.md                          # Project instructions & architecture reference
  README.md                          # Repository overview & usage documentation
  LICENSE                            # MIT License (lowdevco)
  .gitignore                         # Environment & build artifacts exclusion rules
  skills/                            # 26 sub-skills
    seo/                             # Main orchestrator skill
      SKILL.md                       # Entry point, routing table, core rules
      references/                    # On-demand knowledge files (17 files)
    seo-audit/SKILL.md               # Full site audit with parallel agents
    seo-page/SKILL.md                # Deep single-page analysis
    seo-technical/SKILL.md           # Technical SEO (9 categories)
    seo-content/SKILL.md             # E-E-A-T and content quality
    seo-content-brief/SKILL.md       # Content brief generation
    seo-schema/SKILL.md              # Schema.org markup detection/generation
    seo-sitemap/SKILL.md             # XML sitemap analysis/generation
    seo-images/SKILL.md              # Image optimization analysis
    seo-geo/SKILL.md                 # AI search / GEO optimization
    seo-agentic/                     # Agent readiness (Lighthouse Agentic Browsing, WebMCP)
      SKILL.md
      references/                    # Lighthouse category, access policy, discovery, WebMCP, vendor matrix
    seo-local/SKILL.md               # Local SEO (GBP, citations, reviews, map pack)
    seo-maps/SKILL.md                # Maps intelligence (geo-grid, GBP audit, reviews, competitors)
    seo-plan/SKILL.md                # Strategic SEO planning
    seo-flow/                        # FLOW framework integration
      SKILL.md
      references/                    # Consolidated prompts library & methodology
    seo-programmatic/SKILL.md        # Programmatic SEO at scale
    seo-competitor-pages/SKILL.md    # Competitor comparison pages
    seo-hreflang/SKILL.md            # International SEO / hreflang
    seo-google/                      # Google SEO APIs
      SKILL.md
      assets/                        # Audit & performance report templates
      references/                    # API reference files (11 files)
    seo-backlinks/SKILL.md           # Backlink profile analysis
    seo-cluster/                     # Semantic topic clustering
      SKILL.md
      references/                    # Clustering methodology, architecture, workflow
      templates/                     # cluster-map.html interactive visualization
    seo-sxo/                         # Search Experience Optimization (SXO)
      SKILL.md
      references/                    # Page-type taxonomy, user stories, personas, wireframes
    seo-drift/                       # SEO drift monitoring
      SKILL.md
      references/                    # Comparison rules (17 rules, 3 severity levels)
    seo-ecommerce/                   # E-commerce SEO
      SKILL.md
      references/                    # Marketplace API endpoints
    seo-dataforseo/SKILL.md          # Live SEO data via DataForSEO MCP
    seo-image-gen/                   # AI image generation for SEO assets
      SKILL.md
      references/                    # Image gen reference files
  agents/                            # 19 specialist subagents
    seo-technical.md                 # Crawlability, indexability, security
    seo-content.md                   # E-E-A-T, readability, thin content
    seo-schema.md                    # Structured data validation
    seo-sitemap.md                   # Sitemap quality gates
    seo-performance.md               # Core Web Vitals, page speed
    seo-visual.md                    # Screenshots, mobile rendering
    seo-geo.md                       # AI crawler access, GEO, citability
    seo-agentic.md                   # Agent readiness, Lighthouse Agentic Browsing
    seo-local.md                     # GBP, NAP, citations, reviews, local schema
    seo-maps.md                      # Geo-grid, GBP audit, reviews, competitor radius
    seo-google.md                    # Google API analyst (CrUX, GSC, GA4)
    seo-backlinks.md                 # Backlink profile analyst (Moz, Bing, CC, verify)
    seo-dataforseo.md                # DataForSEO data analyst
    seo-image-gen.md                 # SEO image audit analyst
    seo-cluster.md                   # Semantic clustering analysis
    seo-sxo.md                       # Search experience optimization
    seo-drift.md                     # SEO drift monitoring
    seo-ecommerce.md                 # E-commerce SEO analysis
    seo-flow.md                      # FLOW framework integration
  schema/                            # Schema.org JSON-LD templates
    templates.json                   # Ready-to-use structured data definitions
  data/                              # Deterministic datasets
    google-updates.json              # Historical algorithm updates reference
  scripts/                           # 56 Python execution scripts
    agentic_check.py                 # Agent-readiness HTTP auditor (robots, llms.txt, Markdown, ARD, WebMCP)
    agentic_fix.py                   # Agent-readiness fix drafter
    agent_ux_check.py                # Agent-friendly page auditor
    analyze_visual.py                # Visual analysis helper
    backlinks_auth.py                # Backlink API credential management (Moz, Bing)
    bing_webmaster.py                # Bing Webmaster Tools API
    capture_screenshot.py            # Playwright screenshots
    commoncrawl_graph.py             # Common Crawl web graph parser (PageRank, in-degree)
    content_humanize.py              # AI-pattern remover (rewrites AI-typical phrasing)
    content_quality.py               # QRG-aligned content quality detector
    content_verify.py                # Claim extractor + citation-gap detector
    crux_history.py                  # CrUX History API (25-week trends)
    dataforseo_costs.py              # DataForSEO cost estimation and budget tracking
    dataforseo_merchant.py           # Google Shopping / Amazon data fetching
    dataforseo_normalize.py          # DataForSEO response normalization utility
    domain_history.py                # Expired-domain heritage check
    drift_baseline.py                # SEO drift baseline capture (SQLite)
    drift_compare.py                 # SEO drift comparison engine (17 rules)
    drift_history.py                 # SEO drift history query
    drift_report.py                  # SEO drift HTML report generator
    fetch_page.py                    # Page fetcher with UA rotation
    ga4_report.py                    # GA4 organic traffic reports
    gbp_deprecation_lint.py          # GBP feature-deprecation linter
    google_auth.py                   # Credential management (OAuth, SA, API key)
    google_report.py                 # PDF/HTML report generator
    gsc_inspect.py                   # URL Inspection (single + batch)
    gsc_query.py                     # Search Console (queries, pages, sitemaps, sites)
    indexing_notify.py               # Indexing API v3 (URL_UPDATED/URL_DELETED)
    indexnow_submit.py               # IndexNow submitter
    iptc_ai_label.py                 # IPTC DigitalSourceType audit/injection for AI imagery
    keywordseverywhere_api.py        # Keywords Everywhere (Open PageRank) backlinks fallback
    keyword_planner.py               # Google Ads Keyword Planner
    lcp_subparts.py                  # LCP subparts breakdown via CrUX API
    lighthouse_agentic.py            # Lighthouse Agentic Browsing fraction reader
    matomo_auth.py                   # Matomo credential management
    matomo_report.py                 # Matomo Reporting API client
    metadata_template.py             # Templated title/description detector
    moz_api.py                       # Moz Link Explorer API (DA/PA, spam, domains, anchors)
    nlp_analyze.py                   # Cloud Natural Language API
    pagespeed_check.py               # PSI v5 + CrUX API
    parasite_risk.py                 # Parasite-SEO risk scanner
    parse_html.py                    # HTML parser for SEO elements
    preload_check.py                 # Speculation Rules / bfcache / prerender / preload detector
    render_page.py                   # Shared headless renderer (SPA-aware, Playwright)
    runtime.py                       # Managed runtime launcher
    schema_ecommerce_validate.py     # Product schema validator
    schema_generate.py               # JSON-LD generators for high-leverage v2 schema types
    seo_updates.py                   # Primary-source Google updates query tool
    sitemap_discovery.py             # Sitemap discovery (robots.txt, common paths)
    sync_flow.py                     # FLOW prompt library sync utility
    ucp_check.py                     # UCP profile auditor
    unlighthouse_run.py              # Unlighthouse CLI wrapper
    url_safety.py                    # Canonical URL/SSRF safety module (validate, DNS-pin, safe fetch)
    validate_backlink_report.py      # Backlink report validation
    verify_backlinks.py              # Backlink existence verification crawler
    youtube_search.py                # YouTube Data API v3
```

## Commands

| Command | Use Case |
|---------|----------|
| `/seo audit <url>` | Full website audit with parallel subagents |
| `/seo page <url>` | Single page analysis |
| `/seo technical <url>` | Technical SEO across 9 categories |
| `/seo content <url>` | E-E-A-T and content quality |
| `/seo content-brief <topic>` | Detailed content brief: keywords, outline, internal links |
| `/seo schema <url>` | Schema markup detection, validation, generation |
| `/seo sitemap <url>` | Sitemap validation |
| `/seo sitemap generate` | Create new sitemap with industry templates |
| `/seo images <url>` | Image optimization |
| `/seo geo <url>` | AI search optimization (GEO) |
| `/seo agentic <url>` | Agent readiness (Lighthouse Agentic Browsing, AI agent access, WebMCP) |
| `/seo local <url>` | Local SEO (GBP, citations, reviews) |
| `/seo maps [command]` | Maps intelligence (geo-grid, GBP audit, competitors) |
| `/seo backlinks <url>` | Backlink profile analysis |
| `/seo cluster <seed>` | SERP-based semantic clustering |
| `/seo sxo <url>` | Search Experience Optimization |
| `/seo drift baseline\|compare\|history <url>` | SEO drift monitoring |
| `/seo ecommerce <url>` | E-commerce SEO |
| `/seo hreflang [url]` | Hreflang and international SEO |
| `/seo plan <type>` | Strategic planning by industry |
| `/seo programmatic [url\|plan]` | Programmatic SEO analysis |
| `/seo competitor-pages [url\|generate]` | Competitor comparison pages |
| `/seo flow [stage] [url\|topic]` | FLOW framework prompts |
| `/seo google [command] [url]` | Google SEO APIs (GSC, PSI, CrUX, GA4) |
| `/seo dataforseo [command]` | Live SEO data |
| `/seo image-gen [use-case] <desc>` | AI image generation |
| `/seo unlighthouse <url>` | Multi-page Lighthouse runner |

## Development Rules

- Keep SKILL.md files under 500 lines / 5000 tokens
- Reference files should be focused and under 200 lines
- Scripts must have docstrings, CLI interface, and JSON output
- Follow kebab-case naming for all skill directories
- Agents invoked via Agent tool, never via Bash

## Security Rules

- **Never commit credentials**: `.env`, `client_secret*.json`, `oauth-token.json`, `service_account*.json` are all in `.gitignore`
- **URL validation**: All scripts that connect to user-supplied URLs must use `scripts/url_safety.py` (`validate_url_strict()` plus the pinned safe request helpers). This blocks private IPs, loopback, metadata endpoints, redirect rebinding, and DNS rebinding.
- **OAuth tokens**: Never store `client_secret` in the token file. Read it from the client_secret.json file at runtime.
- **No hardcoded paths**: Use `os.path.dirname(os.path.abspath(__file__))` for relative paths, never a user-specific absolute path
- **Config location**: `~/.config/claude-seo/google-api.json` and `~/.config/claude-seo/backlinks-api.json` (user-space, not in repo)

## Report Generation Rules

- **All SEO reports must use `scripts/google_report.py`** as the canonical report generator
- **Dependencies**: `matplotlib>=3.8.0` (charts) + `weasyprint>=70.0` (HTML-to-PDF)
- **Format**: A4 PDF via WeasyPrint + matplotlib charts at 200 DPI
- **Style**: Clean white title page with navy (#1e3a5f) accent, Times New Roman body font
- **Color palette**: Navy #1e3a5f (headers), dark gold #b8860b (accents), forest green #2d6a4f (pass), warm amber #d4740e (warnings), deep red #c53030 (fail), warm cream #faf9f7 (backgrounds)
- **Structure**: Title page → TOC with scores → Executive Summary → Data sections → Recommendations → Methodology
- **Charts**: 85% width, max-height 120mm, figure captions on every chart, saved to `charts/` at 200 DPI
- **No `page-break-inside: avoid`** on any element (causes white gaps in WeasyPrint)
- **Cross-skill enforcement**: After completing ANY analysis command (audit, page, technical, content, schema, geo, local, maps), offer: "Generate a PDF report? Use `/seo google report`"
- **Google logo** appears on title page when using Google API data ("Powered by Google APIs")

## Key Principles

1. **Progressive Disclosure**: Metadata always loaded, instructions on activation, resources on demand
2. **Industry Detection**: Auto-detect SaaS, e-commerce, local, publisher, agency
3. **Parallel Execution**: Full audits spawn up to 17 subagents simultaneously
