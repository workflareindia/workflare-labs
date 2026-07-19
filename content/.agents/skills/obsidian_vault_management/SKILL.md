---
name: obsidian_vault_management
description: Manage an Obsidian vault inside the Quartz content folder, optimizing link integrity, YAML frontmatter, and assets.
---

# Obsidian Vault Management for Quartz

This skill provides guidelines and procedures for working with Markdown files in this Obsidian-compatible vault, optimized for Quartz static site generation.

## Note Organization & Filenames
- **Filenames**: Avoid special characters in filenames. Use alphanumeric characters, hyphens, or spaces.
- **Directories**: Keep related notes grouped in logical subdirectories (e.g., `projects/`, `reference/`).
- **Attachments**: All images, PDFs, and non-markdown media files must be placed in the `attachments/` folder.

## Frontmatter Schema
Every content markdown file (except possibly simple stubs) should begin with a YAML frontmatter block containing metadata parsed by Quartz:

```yaml
---
title: "Setting up Nginx Proxy Manager"
description: "A complete guide to configuring Nginx Proxy Manager for your home server."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---
```

### Frontmatter Fields:
- `title`: String. If omitted, Quartz defaults to the filename.
- `description`: String. Used for description meta tags.
- `date`: YYYY-MM-DD format. Used to sort posts chronologically.
- `ytUrl`: URL string pointing to an accompanying YouTube walkthrough.




## Using Templates
- **Guide Template**: A standard template is located at [[templates/guide-template|templates/guide-template.md]]. Always use this structure when initializing new selfhosting or system guides to ensure consistency.
- **Index Template**: A template for index pages is located at [[templates/index-template|templates/index-template.md]]. Use this structure when creating new index pages or homepages.



## Links & Attachments
- **Wikilinks**: Use standard Wikilinks `[[Note Name]]` or alias links `[[Note Name|Display Text]]` for internal linking.
- **Embedded Images**: Embed images using wikilink syntax: `![[Image Name.png]]` or `![[attachments/Image Name.png]]`.
- **Case Sensitivity**: Wikilink targets are case-insensitive in Obsidian but should ideally match the target file exactly to ensure compatibility across all environments.
