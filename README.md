# Installation-Guides

This repository contains a set of install and basic-use guides for a variety of database / data management and manipulation tools.

The guides are written by the Research Methods Support team for the Collaborative Crop Research Programme.

## Dev Notes

### Previewing Locally

`bundle exec jekyll serve`
navigate to: http://localhost:4000/Installation-Guides/

### Adding Pages

Pages can essentially sit in any folder structure, as their url is defined in the top 'front-matter' (see example on guides/GoogleCloud)
To link a page within the existing navigation system it should be added to \_data/pagelist.yaml.

### Troubleshooting

Q. Why does my scss have errors (deprecated)?
A. If you are using VSCode then linter will throw errors due to jekyll front matter at top of scss,
see http://talk.jekyllrb.com/t/fixing-vscode-scss-linting-errors-on-front-matter/1710 to fix

### General Updates

**2018-11-08:** We are trialling display of the site through github pages and jekyll. To preview locally [install jekyll](https://jekyllrb.com/docs/installation) and then run `bundle install` to install dependecies. Preview the site with:

```
bundle exec jekyll serve
```

You can also view the live site at: https://stats4sd.github.io/Installation-Guides/

Note this also makes available option to link to github for repo info or direct edit links
http://jekyll.github.io/github-metadata/

https://help.github.com/articles/repository-metadata-on-github-pages/

**2018-10-31:** We're using Github mainly as a collaboration tool, to make it easier for the RMS team to collaborate on building these guides. Github can also be a good way of sharing the installation guides, although eventually these should be put somewhere else (in our main Resources Repository) to allow people unfamiliar with Github to easily access them.

The master branch should ideally be kept for completed guides. We have a 'drafts' branch, which exists to save incomplete and un-reviewed documents.

All the documents here are written in Markdown. I recommend [Pandoc](https://pandoc.org/) as a good way of converting markdown files to pdf. It embeds the images linked in the format `![](image-name.png)` (Like in the Heidi and MySQL installation guide). I think there's also a way of pre-configuring styles to get nicer fonts and stuff - there's probably some way of using latex templates or something like that... (if anyone has any exmamples of formatting pdfs with pandoc, please get in touch!)
