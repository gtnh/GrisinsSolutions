# Adding blog posts

## 1. Create a Markdown file

Copy [the blog post template](blog-post-template.md) into `_posts/`, rename it using the format below, and replace its title, description, date and body. The template itself is excluded from the website.

Add a file to `_posts/` using this exact filename format:

```text
YYYY-MM-DD-short-post-title.md
```

For example, `_posts/2026-11-04-evaluating-an-ai-prototype.md`.

## 2. Add front matter and write the article

Start the file with YAML front matter between `---` lines:

```markdown
---
title: "Evaluating an AI prototype"
description: "How to decide whether a prototype is ready for the next step."
date: 2026-11-04 09:00:00 +0100
---

Start with a short introduction.

## Define success first

Write the body using normal Markdown. Use `##` for main sections:
the page already displays the title as its first-level heading.

- Agree on the target outcome.
- Establish a baseline.
- Evaluate on representative examples.

[Get in touch](mailto:pjotrs@grisins-solutions.ch) to discuss a project.
```

The `post` layout is applied automatically. `description` is displayed as the subtitle in the blog listing and used in social metadata. Below it, the listing automatically shows the first paragraph of the post, including links and formatting. If you omit `description`, the listing shows the title followed by the first paragraph. Quote titles and descriptions containing colons. Use `+0100` for Swiss winter time or `+0200` for summer time.

## 3. Add images if needed

Put images in `assets/images/posts/`, then reference them with Jekyll’s `relative_url` filter so links work both locally and on GitHub Pages:

```liquid
![A meaningful description of the image]({{ '/assets/images/posts/my-image.jpg' | relative_url }})
```

Keep images reasonably sized and supply descriptive alt text. For internal page links use the same filter:

```liquid
[About me]({{ '/about/' | relative_url }})
```

## 4. Preview

From the repository root:

```sh
bundle exec jekyll serve --baseurl ""
```

Open <http://127.0.0.1:4000/blog/> and check the article, headings, images and links at desktop and mobile widths. Posts appear automatically, newest first. The URL follows `/blog/YYYY/MM/DD/short-post-title/`.

## 5. Publish

Commit the post and its images, then push to the publishing branch (`main` in the included workflow). GitHub Actions rebuilds and deploys the site. Check the Actions tab for the result.

Future-dated posts are hidden by default. They require a new build on or after their publication time; GitHub Pages does not automatically schedule a rebuild for each date. To preview future posts locally, add `--future`.

## Drafts

Keep unfinished work in `_drafts/short-post-title.md` (no date in the filename) with the same front matter. Preview with:

```sh
bundle exec jekyll serve --baseurl "" --drafts
```

Drafts are not included in the normal production build. To publish, move the file into `_posts/`, add a date to the filename and set the final publication date in the front matter.

See the [official Jekyll post documentation](https://jekyllrb.com/docs/posts/) for more options.
