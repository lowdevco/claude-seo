# Claude SEO: Universal SEO Analysis Skill

## Project Overview

This repository contains **Claude SEO**, a comprehensive SEO analysis skill for Claude. It follows the Agent Skills open standard and a modular architecture. 26 sub-skills, 19 sub-agents, schemas, and a knowledge reference system cover technical SEO, content quality, schema markup, image optimization, sitemap architecture, AI search optimization (GEO), local SEO (GBP, citations, reviews, map pack), maps intelligence, semantic topic clustering, search experience optimization (SXO), SEO drift monitoring, e-commerce SEO, and international SEO.

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

## Development Rules

- Keep SKILL.md files under 500 lines / 5000 tokens
- Reference files should be focused and modular
- Follow kebab-case naming for all skill directories
- Agents invoked via Agent tool or subagent delegation

## Key Principles

1. **Progressive Disclosure**: Metadata always loaded, instructions on activation, resources on demand
2. **Industry Detection**: Auto-detect SaaS, e-commerce, local, publisher, agency
3. **Parallel Execution**: Full audits delegate across specialist subagents simultaneously
