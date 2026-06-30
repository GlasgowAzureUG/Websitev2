# Glasgow Azure User Group website


Some hints to help when updating the site later:

- I've used the Blog section to great a past events section as the formatting was really nice. Couldn't change it from Blog to Past Events in the folder structure.  But that's the past events section. 

- The footer menu has a right hand side menu as well, so if you need three menus you can use that.  I've just deleted everything for that section at the moment so it's not showing.  You can edit the footer menu in the menus.en.toml file. 

- The params.toml file is where a lot of thing are defined, header logo, favicon, social media icons etc. Google analytics etc. 

- hugo.toml is the file you want if you want to change the colour scheme of the site.  I changed the color_primary and light colours fron the original green to a more azure related blue. 

- The contact page uses a form that uses Formspree to help make it work. 

- There is a devcontainer file that will open up a Ubuntu Dev Container within VS Code with Git, Go and Hugo Extended installed to help with editing etc. 

- The sitemap needs updated under layouts\_default\sitemap.xml

## Site-wide announcement bar

There's a dismissible-style announcement bar that appears above the navigation on every page. It's used for important community-wide news (e.g. organiser changes, event updates).

- **Toggle it on/off**: edit the `[announcement]` block in `config/_default/params.toml` and set `enable = true` or `enable = false`.
- **Change the wording, label, or CTA**: edit the same `[announcement]` block (`label`, `text`, `cta`, `link` fields).
- **Edit the full announcement page**: it lives at `content/english/announcement.md` and is published at `/announcement/`.
- **Styling**: the bar's CSS lives in `assets/scss/custom.scss` (Azure-blue gradient). The theme's `style.scss` already imports `custom.scss`, so any tweaks made there will be picked up on the next Hugo build.
- **Layout files**: the bar is rendered by `layouts/partials/announcement-bar.html` and included via the project-level override `layouts/_default/baseof.html` (so the vendored theme isn't modified).