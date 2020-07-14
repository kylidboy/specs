## Install

```sh
git clone https://github.com/filecoin-project/specs.git
cd next # until we move this top level
yarn install
```

## Develop

### Update submodules
```sh
git submodule update --init
```

### Serve with Live Reload
```sh
yarn serve
# open http://localhost:1313/ in the browser
```
# Shortcodes
### `Mermaid`
```html
<!-- Relative path -->
{{< mermaid file="full-deals-on-chain.mmd" />}}

<!-- From hugo content folder -->
{{< mermaid file="/intro/full-deals-on-chain.mmd" />}}

<!-- Inline -->
{{< mermaid >}}
graph TD
  A[Christmas] -->|Get money| B(Go shopping)
  B --> C{Let me think}
  C -->|One| D[Laptop]
  C -->|Two| E[iPhone]
  C -->|Three| F[fa:fa-car Car]
		
{{</ mermaid >}}
```

### `svg`
This shortcode includes zoom and pad feature.
```html
<!-- Relative path -->
{{< svg src="pull-flow.mmd.svg" title="Data Transfer - Pull Flow" >}}

<!-- From hugo content folder -->
{{< svg src="systems/pull-flow.mmd.svg" title="Data Transfer - Pull Flow" >}}
```

### `hint`
```md
{{< hint [info|warning|danger] >}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{< /hint >}}
```
### `figure`
```md
{{< figure src="diagrams/pieces.png" title="Pieces, Proving Trees, and Piece Data Structures" zoom="true">}}
```

### `embed`
```md
# src relative to the page
{{< embed src="piece_store.id" lang="go" >}}

# src relative to content folder
{{< embed src="/systems/piece_store.id" lang="go" >}}
```


# Frontmatter
```md
title: Libraries
description: Libraries used from Filecoin
weight: 3
bookCollapseSection: true
bookhidden: true
dashboardAudit: 1
dashboardState: wip
dashboardInterface: stable
```

# Code fences

They should **always** have a lang, if you don't know or don't care just use `text`

```text

```text
Random plain text context ...
``

```
# Document header
The first heading should be # Head with the dashs like below and should refer to the overall title of the document. The left nav **only** start on the second level of headings. 

```md
---
title: Storage Power Actor
---

# Storage Power Actor
---

## Header for a section in this document
Some text

### Sub header for the previous section

## Another top level header
```


# References
## Markdown links 
These links use "portable links" just like `relref` so you can just give it the name of the file and it will fetch the correct relative link and title for the `<a href="/relative/path" title="page title">` automatically.
You can override the `<a>` title by passing a second `string` in the link definition.

**Note**: When using anchors the title can't be fetched automatically.
```md
[Storage Power](storage_power_consensus)
# <a href="/systems/filecoin_blockchain/storage_power_consensus" title="Storage Power Consensus">Storage Power</a>

[Storage Power](storage_power_consensus "Title to override the page original title")
# <a href="/systems/filecoin_blockchain/storage_power_consensus" title="Title to override the page original title">Storage Power</a>

[Tickets](storage_power_consensus#the-ticket-chain-and-drawing-randomness "The Ticket chain and drawing randomness")
# <a href="/systems/filecoin_blockchain/storage_power_consensus#the-ticket-chain-and-drawing-randomness" title="The Ticket chain and drawing randomness">Tickets</a>

```

## Hugo Cross Refs
Check Hugo's documentation [here](https://gohugo.io/content-management/shortcodes/#ref-and-relref)
```md
[Random]({{<relref "randomness">}})
[Pledge Collateral]({{<relref "storage_power_actor#pledge-collateral">}})
```
## Link shortcode
Theres also `link` shortcode which will fetch the title of the page automatically and use it for the `<a>` text and title, but **DOES NOT** work with anchors (`#anchor-id`)
```md
{{<link storage_power_consensus>}}
# <a href="/systems/filecoin_blockchain/storage_power_consensus" title="Storage Power Consensus">Storage Power Consensus</a>
```

## References
- [hugo theme book](https://themes.gohugo.io//theme/hugo-book/docs/shortcodes/columns/)
- [Katex](https://katex.org/)
- [Mermaid](https://mermaid-js.github.io/mermaid/#/)
  - [config](https://github.com/mermaid-js/mermaid/blob/master/docs/mermaidAPI.md#mermaidapi-configuration-defaults)
  - [editor](https://mermaid-js.github.io/mermaid-live-editor)
- [Pan/Zoom for SVG](https://github.com/anvaka/panzoom)
- [Icons](https://css.gg/)
- [Working with submodules](https://github.blog/2016-02-01-working-with-submodules/)