# Glasgow Azure User Group webiste


Some hints to help when updating the site later:

- I've used the Blog section to great a past events section as the formatting was really nice. Couldn't change it from Blog to Past Events in the folder structure.  But that's the past events section. 

- The footer menu has a right hand side menu as well, so if you need three menus you can use that.  I've just deleted everything for that section at the moment so it's not showing.  You can edit the footer menu in the menus.en.toml file. 

- The params.toml file is where a lot of thing are defined, header logo, favicon, social media icons etc. Google analytics etc. 

- hugo.toml is the file you want if you want to change the colour scheme of the site.  I changed the color_primary and light colours fron the original green to a more azure related blue. 

- The contact page uses a form that uses Formspree to help make it work. 

- There is a devcontainer file that will open up a Ubuntu Dev Container within VS Code with Git, Go and Hugo Extended installed to help with editing etc. 