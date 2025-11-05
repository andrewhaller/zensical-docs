---
icon: lucide/search
tags:
  - Setup
  - Search
---

# Search

Zensical offers seamless client-side search functionality, eliminating the need
to integrate third-party services that may not comply with privacy regulations. Additionally, the search works [offline], enabling you to distribute
documentation as a download.

!!! info "We're interested in your feedback"

    Zensical ships a completely new search engine that we've written from
    scratch and we're eager to hear your feedback! We're continuously working
    on it, and will release it as a [standalone Open Source project] in 2026.

  [offline]: offline.md
  [standalone Open Source project]: https://zensical.org/about/roadmap/#search-and-discovery

## Configuration

The built-in search module is seamlessly integrated with Zensical,
adding multilingual client-side search, and is enabled by default, so there's
not need for additional configuration.

### Search highlighting

When search highlighting is enabled and a user clicks on a search result,
Zensical will highlight all occurrences after following the link.
Add the following lines to `mkdocs.yml`:

=== "`zensical.toml`"

    ``` toml
    [project.theme]
    features = [
        "search.highlight"
    ]
    ```

=== "`mkdocs.yml`"

    ``` yaml
    theme:
      features:
        - search.highlight
    ```

  [Search highlighting example]: ../authoring/code-blocks.md?h=code+blocks

## Usage

### Search exclusion

#### Exclude a page

Pages can be excluded from search with the front matter `search.exclude`
property, removing them from the index. Add the following lines at the top of a
Markdown file:

``` yaml
---
search:
  exclude: true
---

# Page title
...
```

#### Exclude a section

When [Attribute Lists] is enabled, specific sections of pages can be excluded
from search by adding the `data-search-exclude` pragma after a Markdown
heading:

``` markdown
# Page title

## Section 1

The content of this section is included

## Section 2 { data-search-exclude }

The content of this section is excluded
```

  [Attribute Lists]: extensions/python-markdown.md#attribute-lists

#### Exclude a block

When [Attribute Lists] is enabled, specific sections of pages can be excluded
from search by adding the `data-search-exclude` pragma after a Markdown
inline- or block-level element:

``` markdown
# Page title

The content of this block is included

The content of this block is excluded
{ data-search-exclude }
```
