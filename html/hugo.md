# HUGO 
Hugo is an open-source framework written in GO for building static web-sites from markdown source files.

## Example tasks
- Building personal and professional blogs.
- Building static documentation sites.

## Core concepts
- **Markdown support**: All content is written in plain text [markdown](https://www.markdownguide.org/) or HTML
- **Optimized for speed**: Hugo renders a large web site in seconds
- **Themes**: A large ecosystem of [pre-made themes](https://themes.gohugo.io/) is available for easy styling. 

## Quick start

```python
# install hugo (ubuntu linux)
sudo snap install hugo

# create an empty web site (mysite)
hugo new site mysite
cd mysite

# create a git repository (needed for hugo theme)
git init

# Clone and download hugo theme (using ananke theme for my site) into themes folder
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke

# Update TOML file with theme specification (*.toml : toms own markup language, similar to *.ini)
echo "theme = 'ananke'" >> hugo.toml

# Start Hugos development server to view the site
hugo server
```
 
## More information
 - [HUGO documentation](https://gohugo.io/documentation/)
 - [Markdown - basic syntax](https://www.markdownguide.org/basic-syntax/)