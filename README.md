# blog.thelabdesk.com

Source for [blog.thelabdesk.com](https://blog.thelabdesk.com).

## Stack

- [Hugo](https://gohugo.io/) static site generator
- [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme (vendored as git submodule)
- Deployed via [Cloudflare Pages](https://pages.cloudflare.com/) on push to `main`

## Local development

```bash
hugo server -D
```

The `-D` flag includes draft posts. Site live-reloads at <http://localhost:1313>.

## Adding a post

```bash
hugo new content/posts/<slug>.md
```

Edit the new file, set `draft: false` when ready, commit, push.

## Updating the theme

```bash
git submodule update --remote --merge themes/PaperMod
```

## License

Content (everything under `content/`): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

Code and configuration: [MIT](LICENSE)