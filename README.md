# pig-web-search

Web search for the pig coding agent: search the web and read pages in pure PHP, with no API key — DuckDuckGo results, a page's readable text, and the live DOM from a headless Chrome for pages built by JavaScript.

[中文](README.zh-CN.md)

## Installation

```bash
pig install git:github.com/owner888/pig-web-search
```

Nothing else for searching and reading pages: no Composer dependencies, no API key. `browse_web_page` also needs Chrome or Chromium on the machine.

Web search was bundled with pig until it became this package. `pig update` removes the old bundled copy and prints the install line above; `disabledExtensions: ["pig-web-search"]` still reaches the package.

## Tools

| Tool | What it does |
| --- | --- |
| `web_search` | Searches DuckDuckGo and returns the top results — title, snippet, URL (`maxResults`, default 5, at most 10) |
| `fetch_web_page` | The readable text of a page, without scripts, navigation and styles (`maxLength`, default 30000 characters, at most 60000). Reads what the server sends, so it is fast |
| `browse_web_page` | Renders the page in a headless Chrome and returns the text of the live DOM after its JavaScript has run — for single-page apps, dashboards and docs sites that `fetch_web_page` returns empty or as a loading shell. A few seconds slower |

### Command

`/search <query>` searches and shows the top five results.

### Chrome

`browse_web_page` starts Chrome headless with a throwaway profile, drives it over the DevTools protocol with pig's own sockets, and removes the profile when it is done. It finds Chrome at `CHROME_PATH` if that is set, then in the usual install locations, then as `google-chrome`, `chromium`, `chromium-browser` or `chrome` on the `PATH`. Without one, the tool says so and the other two still work.

## Development

The tests run against a pig checkout:

```bash
PIG_DIR=~/path/to/pig ~/path/to/pig/vendor/bin/phpunit -c phpunit.xml
```

`PIG_DIR` defaults to a `pig` directory next to this package. The test that renders a page needs Chrome and is skipped without it.

## License

MIT — see [LICENSE](LICENSE).
