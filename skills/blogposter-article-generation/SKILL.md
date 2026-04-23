---
name: BlogPoster Article Generation & Deployment
description: Generate unique SEO-optimized articles for 3 Swedish websites and deploy to Netlify
author: BlogPoster Team
version: 1.0.0
applies_to:
  - "**/*.md"
keywords:
  - article-generation
  - netlify-deployment
  - seo-optimization
  - blog-automation
---

# BlogPoster: Article Generation & Netlify Deployment Skill

## Purpose
Generate 2 unique, SEO-optimized articles for each of 3 Swedish websites (Mintborste.se, Lokalmokare.se, Bytbilnu.se), add them to respective local folders, and deploy to their Netlify projects.

## Prerequisites
- Local folder structure: `~/Desktop/blogs/mintborste/`, `~/Desktop/blogs/lokalmokare/`, `~/Desktop/blogs/bytbilnu/`
- Netlify CLI authenticated with `netlify login`
- Each Netlify project linked (`.netlify/state.json` exists in each folder)
- Existing articles in each folder to analyze for style/keywords

## Workflow

### Phase 1: Analyze Existing Content
For each site:
1. **Scan existing articles** in the local folder
2. **Extract keywords, tone, topics** from existing articles
3. **Document findings** (3-5 main keywords per site, style notes)
4. **Check for gaps** - what topics are NOT covered?

### Phase 2: Generate New Articles
For each site:
1. **Choose 2 unique topics** that:
   - Fit the site niche (dentist/toothbrush, local car rental, car buying)
   - Use appropriate keywords (NOT long-tail, competitive keywords)
   - Don't overlap with existing articles
   - Match existing article style/length
2. **Generate article 1**: ~1000-1500 words, SEO-optimized
3. **Generate article 2**: Different topic, same quality/length
4. **Verify uniqueness**: Compare against all existing articles to ensure no duplication

### Phase 3: Quality Checks
Before deployment, verify:
- [ ] No keyword duplication across the 2 new articles
- [ ] No content similarity with existing articles (>10% similarity rejected)
- [ ] Articles match existing style, formatting, H2/H3 structure
- [ ] Swedish language quality (if applicable)
- [ ] Approx. 1000-1500 words each
- [ ] Keywords naturally integrated (NOT stuffed)

### Phase 4: Add to Folders
For each site:
1. Save article 1: `~/Desktop/blogs/[site]/[date]-article-1-[keyword].md`
2. Save article 2: `~/Desktop/blogs/[site]/[date]-article-2-[keyword].md`
3. Update site's article index/TOC if needed

### Phase 5: Deploy to Netlify
For each site:
```bash
cd ~/Desktop/blogs/[site]
netlify deploy --prod
```

## Decision Points

**Q: Should we regenerate if an article fails quality checks?**
- Yes, regenerate with different topic/keywords and re-check

**Q: What if keywords are hard to find for a niche?**
- Research 5-7 medium-difficulty keywords, pick the 2-3 most relevant per article

**Q: Should articles link to each other?**
- No, keep each site's content independent

## Completion Checklist
- [x] Analyzed existing content from all 3 sites
- [x] Extracted keywords and style patterns
- [x] Generated 2 articles per site (6 total)
- [x] Verified no duplication within site and across sites
- [x] Added all articles to correct folders
- [x] Deployed to Netlify for all 3 sites
- [x] Verified articles live on deployed sites

## Example Command
```bash
# When ready to deploy
for site in mintborste lokalmokare bytbilnu; do
  cd ~/Desktop/blogs/$site
  netlify deploy --prod
done
```

## Notes
- Run this skill each time you want to add new articles
- Always check existing articles first to prevent duplication
- Keywords should be research-based, not guesses
- Maintain consistent quality and length across all sites
