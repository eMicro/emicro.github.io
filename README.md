# eMicro — Hugo + GitHub Pages

Persian-first bilingual (FA/EN) website and blog. The existing eMicro landing page is retained as the Hugo home layout. The blog is published at `/blog/` (Persian) and `/en/blog/` (English).

## Requirements

- Hugo Extended 0.169.0 or compatible
- Git

## Local development

```bash
hugo server -D
```

Open http://localhost:1313/. Blog: http://localhost:1313/blog/ and http://localhost:1313/en/blog/.

## Publish

1. Copy the contents of this folder into the root of `eMicro/emicro.github.io`.
2. Commit and push to `main`.
3. In GitHub repository Settings → Pages, set **Build and deployment → Source** to **GitHub Actions**.
4. Open Actions and wait for `Build and deploy Hugo site to GitHub Pages` to complete.
5. Keep the verified custom domain `emicro.ir` configured in Settings → Pages.

The workflow builds `public/` and deploys it as a Pages artifact. Do not commit `public/`; Hugo generates it during CI. The `cname` setting generates the `CNAME` file for `emicro.ir`.

## Write a new article

Create two files with the same base name and language suffix in `content/blog/`, for example:

- `my-new-post.fa.md`
- `my-new-post.en.md`

Use the same `translationKey` in both front matters to connect the translations. Set `draft: false` when ready to publish. A front matter example:

```yaml
---
title: "عنوان مقاله"
date: 2026-11-09
description: "خلاصه کوتاه مقاله"
translationKey: "my-new-post"
categories: ["IoT"]
tags: ["MQTT", "ESP32"]
draft: false
---

متن مقاله با Markdown...
```

## Notes

- No database, CMS, or JavaScript build tool is required.
- The homepage is preserved from the previous static eMicro landing page and now links to the blog.
- The blog has a dark, responsive layout and language switcher.
