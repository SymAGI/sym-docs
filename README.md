# SymAGI Docs Repository

Dit zijn mijn notities voor het beheren van de SymAGI documentatiesite.

De publieke documentatiesite staat in:

```text
/docs
```

GitHub Pages is ingesteld op:

```text
Branch: main
Folder: /docs
Custom domain: docs.symagi.com
```

## Links tussen pagina's

Binnen Jekyll kun je naar andere Markdown-bestanden linken met:

```markdown
[Installation]({% link getting-started/installation.md %})
```

Dit verwijst naar het bestand:

```text
/docs/getting-started/installation.md
```

Omdat `/docs` de root van de GitHub Pages-site is, hoef je `docs/` zelf niet in de link te zetten.

## Link naar een hoofdstuk

Een heading kan een vaste anchor krijgen:

```markdown
## Overview
{: #overview }
```

Daarna kun je binnen dezelfde pagina linken met:

```markdown
[Overview](#overview)
```

Of vanuit een andere pagina:

```markdown
[Getting Started overview]({% link getting-started.md %}#overview)
```

## Voorbeeld: parent-pagina `getting-started.md`

```markdown
---
title: Getting Started
layout: default
nav_order: 10
has_children: true
---

# Getting Started

This section helps you get started with SymAGI.

## Overview
{: #overview }

SymAGI consists of several components:

- Sym Core
- Sym Agent
- Public APIs

## Next steps
{: #next-steps }

Start with the [installation guide]({% link getting-started/installation.md %}).

Or jump directly to the [system requirements]({% link getting-started/installation.md %}#system-requirements).
```

## Voorbeeld: child-pagina `getting-started/installation.md`

```markdown
---
title: Installation
layout: default
parent: Getting Started
nav_order: 10
---

# Installation

This page explains how to install and prepare SymAGI.

## System requirements
{: #system-requirements }

Before installing SymAGI, make sure your environment meets the basic requirements.

- Git
- A supported runtime
- Access to the required repositories

## Installation steps
{: #installation-steps }

Follow these steps to install SymAGI.

1. Clone the repository.
2. Configure the environment.
3. Start the runtime.

## Related pages
{: #related-pages }

Go back to [Getting Started]({% link getting-started.md %}).

Or jump back to the [Getting Started overview]({% link getting-started.md %}#overview).
```

## Just the Docs navigatie

Een parent-pagina krijgt:

```yaml
has_children: true
```

Een child-pagina krijgt:

```yaml
parent: Getting Started
```

De waarde van `parent` moet overeenkomen met de `title` van de parent-pagina.

De volgorde in het menu wordt bepaald met:

```yaml
nav_order: 10
```

Gebruik bij voorkeur stappen van 10, zodat er later makkelijk pagina's tussen kunnen.
