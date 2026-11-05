# Grišins Solutions

Professional website for Dr. Pjotrs Grišins, built with Jekyll for GitHub Pages. Includes Home, About, Blog, Contact and a custom 404 page. No JavaScript or externally hosted fonts are required.

## Preview locally

Install Ruby 3.2 or newer and Bundler, then run:

```sh
bundle install
bundle exec jekyll serve --baseurl ""
```

Open <http://127.0.0.1:4000>. The empty base URL is only a local override; the repository’s GitHub Pages path remains configured in `_config.yml`.

## Publish on GitHub Pages

A GitHub Actions workflow is included in `.github/workflows/pages.yml`.

1. In the repository’s **Settings → Pages → Build and deployment**, choose **GitHub Actions** as the source.
2. Push the website to the `main` branch (or adjust the branch in the workflow).
3. The workflow builds the site and deploys the generated `_site` directory. It can also be run manually from the Actions tab.

The current configuration targets <https://gtnh.github.io/GrisinsSolutions/> based on this repository’s remote. If the repository name or owner changes, update `url` and `baseurl` in `_config.yml`.

For a custom domain, set `url` to the full HTTPS origin and `baseurl` to `""`, configure the domain in GitHub Pages, and follow GitHub’s DNS instructions. A custom domain has not been assumed from the email address.

## Edit the website

- `index.html`: homepage services, selected experience and approach
- `about.html`: professional profile
- `contact.html`: contact page
- `blog.html`: automatic post listing, currently empty
- `_config.yml`: contact details, site URL and shared metadata
- `_layouts/` and `_includes/`: shared page structure
- `assets/css/style.css`: responsive styling
- `assets/images/pjotrs-grisins.jpg`: optimized copy of the supplied portrait
- [Blog authoring guide](docs/adding-blog-posts.md)
- [Blog post template](docs/blog-post-template.md)

The source notes (`cv.md`, `roles.md`, `goal.md`, `AI_Engineer.md`) and authoring documentation are explicitly excluded from the generated website. Git ignore rules do not control Jekyll’s output; keep exclusions in `_config.yml` up to date if you add private working notes. Files in a public Git repository remain accessible through GitHub.

## Content notes

The copy is based on the supplied CV and role notes. The shared ChatGPT conversation could not be retrieved during implementation. The CV contains conflicting PhD completion years, so the public profile deliberately omits the year. Selected projects are described as prior employment experience, not independent client engagements.

## Verification

```sh
bundle exec jekyll build --strict_front_matter
```

Official references: [GitHub Pages with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll), [Jekyll posts](https://jekyllrb.com/docs/posts/).
