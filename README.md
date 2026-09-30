# sudo-yashbhardwaj.github.io

Personal site of Yash Bhardwaj, built with Jekyll and published by GitHub Pages at
<https://sudo-yashbhardwaj.github.io>.

## Where things live

| What | Where |
|---|---|
| Homepage (bio, publications, projects, experience, awards) | `_pages/home.html` |
| One file per paper | `_publications/*.md` |
| One file per project | `_portfolio/*.md` (`published: false` hides one; `order` sets its position) |
| Page shell, nav, footer, theme toggle | `_layouts/base.html` |
| Paper and project write-up layout | `_layouts/entry.html` |
| Card shown on the homepage for each paper or project | `_includes/card.html`, driven by each file's front matter |
| Stylesheet | `assets/css/site.css` (adapted from Ye Mao's site, with permission; site-specific rules follow the original block) |
| Card and page figures | `images/work/` |
| Originals the figures are cut from (not published) | `_sources/` |
| CV | `files/Yash_Bhardwaj_VIS.pdf` (linked from `author.cv` in `_config.yml`) |

Author-facing reminders can be left in a page with `{% include todo.html text="..." %}`; they render only
under `jekyll serve`, never in the published site.

## Running locally

Needs Ruby 3.3 (`brew install ruby@3.3`) and Bundler.

```bash
export PATH=/opt/homebrew/opt/ruby@3.3/bin:$PATH
bundle config set --local path vendor/bundle
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000>. Edits to pages rebuild automatically; edits to `_config.yml` need a restart.

To check the site exactly as GitHub Pages publishes it (no author-facing reminders), build with `JEKYLL_ENV=production bundle exec jekyll build` and open `_site/index.html`.
