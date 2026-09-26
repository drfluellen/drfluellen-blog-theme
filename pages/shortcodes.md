{{< newthought >}}This theme adds eleven shortcodes{{< /newthought >}} for the things Edward Tufte's books do well: notes in the margin, figures that break the column, epigraphs, and poetry. Every example below was tested with Hugo 0.158. The notes in the margin record where this version of the theme differs from its original README.

Every shortcode opens with `{{</* name */>}}` and closes with `{{</* /name */>}}`.

## Notes in the margin

### sidenote

A numbered note in the right margin, like a footnote you don't have to scroll for.{{< sidenote >}}Like this one. On a phone, tap the number to open it.{{< /sidenote >}} The theme numbers notes automatically.

```
Augustine’s restlessness{{</* sidenote */>}}*Conf.* I.1.1.{{</* /sidenote */>}} frames the whole work.
```

No label is needed; the README's `{{</* sidenote "label" */>}}` form still works but isn't required.{{< marginnote >}}Keep each note to a single paragraph. A blank line inside a note breaks the layout.{{< /marginnote >}} Markdown such as italics and links works inside.

### marginnote

The same as a sidenote, but with no number. On a phone it hides behind a ⊕ you can tap.

```
The Rule sets the hours of prayer.{{</* marginnote */>}}See RB 16–18.{{</* /marginnote */>}}
```

## Figures

### figure

An image in one of three layouts, chosen with `type`:

- **Regular** (no `type`): the image is as wide as the text, with the caption in the margin.
- **`type="margin"`**: the image and caption both sit in the margin.
- **`type="full"`**: the image runs across the text and the margin, with the caption underneath.

```
{{</* figure src="https://…/abbey.jpg" alt="Abbey basilica" title="Fig. 1." caption="Mary Help of Christians Basilica." label="abbey-2026-09" */>}}

{{</* figure type="margin" src="https://…/chester.jpg" alt="Chester the cat" caption="Chester, unimpressed." label="chester-2026-09" */>}}

{{</* figure type="full" src="https://…/campus.jpg" alt="Campus panorama" caption="The quad in September." attr="Photo: D. Williams" attrlink="https://www.drfluellen.blog/" */>}}
```

| Parameter | Does |
|---|---|
| `src` | Image URL (required) |
| `alt` | Description for screen readers |
| `type` | `margin` or `full`; leave it out for regular |
| `title` | Bold lead-in before the caption |
| `caption` | Caption text |
| `label` | ID for the mobile ⊕ toggle; needed for regular and margin |
| `attr`, `attrlink` | Credit text and its link |
| `link` | Makes the image itself a link (not in the README) |
| `class` | CSS class on a regular figure (not in the README) |

Make every `label` unique across the whole blog, not just within one post.{{< sidenote >}}Figure labels are used exactly as written. The home page shows several posts at once, so two posts that both use `label="fig1"` will make the ⊕ toggles open the wrong figure. Adding the date, as in `chester-2026-09`, avoids this.{{< /sidenote >}}

## Quotation

### blockquote

An indented quotation with an optional attribution line, built from `pre`, then `cite` (in italics, linked if you give `link`), then `post`.

```
{{</* blockquote pre="Augustine," cite="Confessions" link="//www.newadvent.org/fathers/110101.htm" post="I.1.1" */>}}Our heart is restless until it rests in you.{{</* /blockquote */>}}
```

{{< blockquote pre="Augustine," cite="Confessions" post="I.1.1" >}}Our heart is restless until it rests in you.{{< /blockquote >}}

Start a `link` with `//`, not `https://`.{{< sidenote >}}A link beginning `https://` comes out as the broken address `#ZgotmplZ`.{{< /sidenote >}} The theme adds no punctuation, so put your own comma or dash in `pre`. The quotation must be a single paragraph; for longer passages, use Markdown's `>` and go without the attribution.

### epigraph

Takes the same parameters as blockquote, but sets the quotation in italics with generous space around it. It suits the opening of an essay or a quotation post. Adding `type="compact"` (not in the README) tightens the spacing between the quotation and its attribution.

```
{{</* epigraph pre="Boethius," cite="Consolation of Philosophy" post="III, m. 9" */>}}To see thee is the end and the beginning.{{</* /epigraph */>}}
```

### cite

Marks a title or source in italics anywhere in the text: {{< cite >}}Ex Corde Ecclesiae{{< /cite >}}.

```
As {{</* cite */>}}Ex Corde Ecclesiae{{</* /cite */>}} puts it…
```

## Text

### newthought

Opens a section in small capitals, as the first line of this page does.

```
{{</* newthought */>}}In the beginning{{</* /newthought */>}} was the Word.
```

### poetry

Keeps your line breaks and sets the lines in the body typeface. A blank line starts a new stanza.

```
{{</* poetry */>}}
Glory be to God for dappled things–
 For skies of couple-colour as a brinded cow;
{{</* /poetry */>}}
```

{{< poetry >}}
Glory be to God for dappled things–
 For skies of couple-colour as a brinded cow;
For rose-moles all in stipple upon trout that swim;
{{< /poetry >}}

Indent with ` ` or ` `, not tabs or spaces.{{< sidenote >}}Contrary to the README, tabs and spaces at the start of a line are removed. A tab on the first line turns the whole poem into a code block.{{< /sidenote >}}

### summary

A synopsis for a long, titled essay. Put `<!--more-->` directly after it, and the home page shows only the summary with a *Continue reading* link.

```
{{</* summary */>}}Why the Benedictine school still teaches the whole person.{{</* /summary */>}}<!--more-->
```

The `<!--more-->` marker controls where the post is cut; the shortcode only styles the summary.{{< marginnote >}}Without the marker, Hugo cuts a titled post off on the home page after about seventy words, wherever that falls. Posts without a title always appear in full.{{< /marginnote >}}

## Structure

### div and section

Each wraps a block of content in an HTML element, with an optional `class` or `id`. Close either one with `"end"`.

```
{{</* div class="sans" */>}}
This paragraph is set in Gill Sans.
{{</* div "end" */>}}

{{</* section "begin" */>}}
A plain section.
{{</* section "end" */>}}
```

With no `class` or `id`, write `"begin"` explicitly.{{< sidenote >}}Under Hugo 0.158, a section or div shortcode with no parameters produces no opening tag at all, so the closing `"end"` has nothing to close.{{< /sidenote >}} Useful classes from the theme: `sans` (Gill Sans), `fullwidth` (across text and margin), `iframe-wrapper` (16:9 video), and `table-wrapper` (wide tables).

## Habits

- **For a post that starts with a shortcode,** open with a hidden line to set its web address: `<p hidden>restless heart quote</p>`. Otherwise Micro.blog builds the address from the shortcode's text.
- **In Ulysses,** wrap each shortcode in tildes so it passes through unchanged.
- **Before crossposting,** look at how a post with margin notes appears in the timeline and on Bluesky, and keep anything essential out of the notes.