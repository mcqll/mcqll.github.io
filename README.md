# MCQLL website
(based on [al-folio](https://github.com/alshedivat/al-folio) theme. See readme there for info (though note, I've switched from Pygments to [Rouge](https://github.com/rouge-ruby/rouge) for code highlighting).

## Getting started

Download this repo to your local machine.
Have [jekyll](https://jekyllrb.com/) and [bundler](https://bundler.io/) installed.

## Editing workflow ! IMPORTANT !

- edit a page locally (for example, edit one of the files in the `_pages/` directory, or add a new `lastname.firstname.md` file to `/_people` to add a new lab member)
- generate the site locally with `bundle exec jekyll serve` (and preview your changes by visiting the URL that generates).
- once you are satisfied with your edits, commit them and then `git push` (note, **this will not be published yet**)
- then you must deploy using `./bin/deploy --user`. This deploys the site to the `master` branch
    - What's going on here? It's a workaround. `master` is where the generated site will live, `source` is for the source code.  When you just run `git push` you will update the source branch. But we want to just put a generated version of the site at the master branch, rather than have GitHub do this automatically. This is because GitHub pages doesn't allow reference to external plugins such as `github-scholar` it seems, so it won't work to just edit the site in the `master` branch and have GitHub do the generation for you.


## Adding/editing the list of members

There is a makdown file for each lab member in the `/_people` directory, with name format `lastname.firstname.md` (this is just to be tidy and for alphabetic ordering when the site is built). 

Add a headshot or two to the `/assets/img/` directory. Then edit the markdown file: at the top of the file there is a short yaml header between two sets of three hyphens,  which should be filled (starting with `layout: person`)

```yaml
---
layout: person
name: # Full Name Here
position: #grad OR undergrad OR faculty OR postdoc OR alum
description: #subtitle, such as Principal Investigator, or Associate
img: # imagename (in the /assets/img/ directory)

profile:
  img: # imagename (in /assets/img) optional, another image for the personal page, if different from the one on the people page
  office: # address, if you want this
  cv: # link to cv
  website: # link to external personal webpage 

---
```
Below this, enter any markdown/html you want.
