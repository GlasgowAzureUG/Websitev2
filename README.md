# Glasgow Azure User Group website


Some hints to help when updating the site later:

- I've used the Blog section to great a past events section as the formatting was really nice. Couldn't change it from Blog to Past Events in the folder structure.  But that's the past events section. 

- The footer menu has a right hand side menu as well, so if you need three menus you can use that.  I've just deleted everything for that section at the moment so it's not showing.  You can edit the footer menu in the menus.en.toml file. 

- The params.toml file is where a lot of thing are defined, header logo, favicon, social media icons etc. Google analytics etc. 

- hugo.toml is the file you want if you want to change the colour scheme of the site.  I changed the color_primary and light colours fron the original green to a more azure related blue. 

- The contact page uses a form that uses Formspree to help make it work. 

- There is a devcontainer file that will open up a Ubuntu Dev Container within VS Code with Git, Go and Hugo Extended installed to help with editing etc. 

- The sitemap needs updated under layouts\_default\sitemap.xml

## Homepage banner image

Set `banner.image` in `content/english/_index.md` to an image path relative to `assets/` (for example, `images/screenshot.svg`). The homepage uses the shared Hugo image partial to publish the asset; using the path directly as an image URL does not copy it into the built site.

## Site-wide announcement bar

There's a dismissible-style announcement bar that appears above the navigation on every page. It's used for important community-wide news (e.g. organiser changes, event updates).

- **Toggle it on/off**: edit the `[announcement]` block in `config/_default/params.toml` and set `enable = true` or `enable = false`.
- **Change the wording, label, or CTA**: edit the same `[announcement]` block (`label`, `text`, `cta`, `link` fields).
- **Edit the full announcement page**: it lives at `content/english/announcement.md` and is published at `/announcement/`.
- **Styling**: the bar's CSS lives in `assets/scss/custom.scss` (Azure-blue gradient). The theme's `style.scss` already imports `custom.scss`, so any tweaks made there will be picked up on the next Hugo build.
- **Layout files**: the bar is rendered by `layouts/partials/announcement-bar.html` and included via the project-level override `layouts/_default/baseof.html` (so the vendored theme isn't modified).

## YouTube recordings

Past event pages use Hugo's `{{< youtube VIDEO_ID >}}` shortcode. The project override in `layouts/shortcodes/youtube.html` preserves the Hugo 0.124.1 shortcode behavior and sets `referrerpolicy="strict-origin-when-cross-origin"` on each player.

YouTube requires an HTTP `Referer` identifying the embedding site. The live site's `Referrer-Policy: same-origin` header otherwise suppresses it for YouTube, causing player configuration Error 153. The iframe policy sends only the site's origin to YouTube without changing the policy for the rest of the page.

After deployment, check a recording on `/blog/2025/` over HTTPS and confirm that the YouTube embed request includes `Referer: https://www.gaug.co.uk/` in the browser's Network panel. Test playback in a browser without referrer-blocking extensions; opening a generated HTML file directly is not a valid playback test.