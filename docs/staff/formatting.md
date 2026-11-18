# Formatting Cheat Sheet

Pages are written in **Markdown**, which is the same formatting Discord uses, with a few extras.

## The basics (same as Discord)

```markdown
**bold**   *italic*   ~~strikethrough~~   `inline code`
```

## Headings

Headings become the "On this page" menu and get their own shareable links.

```markdown
# Page title (one per page)
## Section
### Sub-section
```

## Links

```markdown
[Text to show](https://example.com)
[Another wiki page](../rules.md)
[A section on another page](../rules.md#roleplay-rules)
```

## Lists

```markdown
- Bullet point
- Another
    - Indented (4 spaces)

1. Numbered
2. List
```

## Tables

```markdown
| Column 1 | Column 2 |
|----------|----------|
| Cell     | Cell     |
```

## Coloured boxes

```markdown
!!! note "Title here"
    Indent the text by 4 spaces.

!!! tip
!!! warning
!!! danger
!!! info
!!! success
!!! question
```

!!! example "What they look like"
    This is an `example` box. Try `tip`, `warning` and the others to see their colours.

## Fold-out boxes

Use `???` instead of `!!!` to make a box that stays closed until clicked:

```markdown
??? note "Click to see spoilers"
    Hidden content here.
```

## Tabs

```markdown
=== "Tab one"

    Content for tab one.

=== "Tab two"

    Content for tab two.
```

## Images

Upload the picture into `docs/assets/`, then:

```markdown
![Description of image](../assets/map.png)
```

## Icons and emoji

```markdown
:dragon:  :crossed_swords:  :scroll:  :material-sword:
```

Result: :dragon: :crossed_swords: :scroll: :material-sword:
