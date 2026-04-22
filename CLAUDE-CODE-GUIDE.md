# Claude Code Quick Reference

A cheat sheet for making changes to the Dawn Knapper website using Claude Code.

## Getting Started

1. Clone the repo locally (one time):
   ```bash
   git clone https://github.com/YOUR-USERNAME/dawn-knapper-website.git
   cd dawn-knapper-website
   ```

2. Launch Claude Code from the project directory:
   ```bash
   claude
   ```

3. After changes are made, push them live:
   ```bash
   git add .
   git commit -m "Brief description of the change"
   git push
   ```

Within about a minute, the site updates at `dawnknapper.info`.

## Golden Rule for Prompts

Always tell Claude Code **which file**, **which section**, and **what to change**. The more specific, the better. Example:

✓ "In `index.html`, in the About section, replace the first paragraph with this new text: [paste]"

✗ "Update the About section"

## Common Tasks

### Text updates

**Change the tagline:**
> In `index.html`, change the tagline under the hero headline from "A thoughtful, compassionate practice..." to "[new tagline]". It's the `.tagline` paragraph inside `.hero-text`.

**Update Dawn's bio:**
> In `index.html`, in the `.about-body` section, replace the three placeholder paragraphs with this new bio from Dawn: [paste bio]. Keep the drop-cap on the first letter of the first paragraph and the "— D.K." signature at the end.

**Change the Rogers quote:**
> In `index.html`, replace the Carl Rogers quote in the `.quote blockquote` section with this new quote: "[new quote]" — [attribution].

### Contact updates

**Add/change email:**
> In `index.html`, in the Contact section, change the `.contact-email` link from `hello@example.com` to `[new email]`. Update both the `href="mailto:"` and the displayed text.

**Add a phone number:**
> In `index.html`, in the `.contact-meta` div, add a phone section below the Response block. Match the existing style with a bold uppercase label followed by the value.

### Visual changes

**Try a different accent color:**
> In `index.html`, change `--accent` and `--accent-deep` in the CSS variables at the top. Try `--accent: [hex]` and `--accent-deep: [hex]`. Keep everything else the same so I can see just the color change.

**Bigger/smaller portrait:**
> In `index.html`, change the `.hero-portrait` `max-width` from 500px to [new value]px.

**Change the script font for her name:**
> In `index.html`, swap the Great Vibes font in the `.mark` logotype for [font name from Google Fonts]. Update both the `<link>` in the head and the `font-family` declaration.

### Adding new content

**Add a new section:**
> In `index.html`, add a new section called "[Section Name]" between [Section A] and [Section B]. Use the same styling patterns as the [existing section]. Add a corresponding link in the nav. Use placeholder content for now.

**Add social/LinkedIn to contact:**
> In `index.html`, in the Contact section, add a LinkedIn link styled like the existing `.contact-email` but smaller and positioned below it.

### Replacing the portrait

> I've replaced `assets/portrait.png` with a new image. Open `index.html` and check whether the `background-position` on `.hero-portrait` (currently `center 25%`) still frames the face well. If not, suggest a better value.

## Tips

- **Commit often.** Small commits with clear messages make it easy to undo something if a change doesn't work out.
- **Preview before pushing.** Open `index.html` in a browser locally to verify changes before running `git push`.
- **Keep a backup of the current working version** before making big changes: `cp index.html index.backup.html`
- **Use branches for experiments.** If you want to try something risky: `git checkout -b experiment` — you can always come back to `main` if it doesn't work out.

## If Something Breaks

- **Check GitHub Pages status.** Repo → Settings → Pages should show a green checkmark and the live URL. If it shows an error, it'll tell you what's wrong (usually a typo in CNAME or a DNS issue).
- **DNS not working?** DNS propagation can take up to 24 hours. Use https://dnschecker.org/ to see if your records have propagated globally.
- **HTTPS certificate error?** Uncheck "Enforce HTTPS" in GitHub Pages settings, wait 10 minutes, then re-check it. GitHub will re-issue the cert.
- **Site showing old content?** Hard refresh the browser (Cmd+Shift+R on Mac, Ctrl+Shift+R on Windows). CDN caches can take a few minutes.

## When in Doubt

Ask Claude Code to explain before it changes:
> Before making any changes, describe what you're planning to do and which files and sections will be affected.

That's a great habit for learning the codebase and catching miscommunications early.
