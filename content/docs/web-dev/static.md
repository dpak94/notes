---
type: "docs"
title: Static Sites
url: "/docs/web-dev/static/"
---

# Static Site Generators

## Hugo

| **`Command`**                      | **`Function`**                      |
| ---------------------------------- | ----------------------------------- |
| `hugo new site <siteName>`         | Create new site using Hugo          |
| `hugo server`                      | Start the hugo server               |
| `hugo server -D`                   | Start the server with drafts loaded |
| `hugo new content <link/fileName>` | Add new page                        |

---

## Jekyll

| **`Command`**               | **`Function`**                                       |
| --------------------------- | ---------------------------------------------------- |
| `jekyll new siteName`       | Create a site and generate relevant sitefiles        |
| `bundle exec jekyll serve`  | Start the server                                     |
| `jekyll serve --livereload` | Live server                                          |
| `jekyll build`              | Builds the static site instead of running the server |
| `jekyll serve --draft`      | Builds the site with draft content included          |

## Important Notes

- Contains layouts to create templates of websites. Use layout within pre-defines layouts to make formats even more interesting without entering data in every HTML/MD page.
- [List of placeholders](https://jekyllrb.com/docs/permalinks/#placeholders)
