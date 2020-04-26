# MCQLL website
The website for the Montreal Computational & Quantitative Linguistics Lab, MCQLL, lives here. See [mcqll.org](https://mcqll.org).

This jekyll-based site was designed off of the [al-folio](https://github.com/alshedivat/al-folio) theme, with modifications. If you wish to make a similar site, see readme there for some info (though note, [I](https://github.com/postylem)'ve switched from Pygments to [Rouge](https://github.com/rouge-ruby/rouge) for code highlighting).

Below is information you should find useful if you are editing the MCQLL site.

## Getting started

Download this repo to your local machine.
Have [Ruby](Ruby), [jekyll](https://jekyllrb.com/) and [bundler](https://bundler.io/) installed.  You might need to install ruby with `brew install ruby`, then update your PATH by running `echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.bash_profile`, and reload with `source ~/.bash_profile`.

Then,
```bash
gem install bundler jekyll github-pages jekyll-email-protect jekyll-scholar unicode_utils
bundle install
```
if it is correctly configured, `bundle exec jekyll serve` should work to serve the site locally.

**NOTE:** Latest version of Jekyll (3.8.3) is not compatible with latest github-pages gem. You'll be able to work with both gems by downgrading Jekyll in your Gemfile to 3.7.3. 

To downgrade jekyll:
In the Gemfile, change `gem 'jekyll'` to `gem 'jekyll', '3.7.3'`. Then, `bundle update`.  This should already be so in the current version of the Gemfile in this repository.

## Editing workflow ! IMPORTANT !

- edit a page locally (for example, edit one of the files in the `_pages/` directory, or add a new `lastname.firstname.md` file to `/_people` to add a new lab member)
- generate the site locally with `bundle exec jekyll serve` (and preview your changes by visiting the URL that generates).
- once you are satisfied with your edits, add and commit your changes and then `git push` (note, **this will not be published yet**)
- you must deploy using `./bin/deploy --user`, and respond `y` to proceed. This deploys the site to the `master` branch
    - What's going on here? It's a workaround. `master` is where the generated site will live, `source` is for the source code.  When you just run `git push` you will update the source branch. But we want to just put a generated version of the site at the master branch, rather than have GitHub do this automatically. This is because GitHub pages doesn't allow reference to external plugins such as `github-scholar` it seems, so it won't work to just edit the site in the `master` branch and have GitHub do the generation for you.

## News: Adding lab talks or other announcements

To add a new item to the News section, create a new document in the `_news/` directory.  For lab meetings, name this file with "meeting" followed by the date, like `meeting-2020-04-22.md`.

Follow this template:

```
---
layout: post
title: April 22nd - Spandana Gella presents 
date: 2020-04-21 8:20:00-0400 # date that this post is added (not presentation date)
inline: false 
---

**Presenter**, will present on *topic* at this week's lab meeting. 

- When: **Wednesday, April 22nd, at 14:00 UTC-4**
- Zoom: [Register for MCQLL meetings beforehand here](https://mcgill.zoom.us/meeting/register/tJArfuitrjksHdAss5v1qiGR5VzCtPtiDm9x)

#### Abstract
<blockquote>
  Abstract here.
</blockquote>

#### Bio
Bio here. 
```

## Adding/editing the list of members

There is a markdown file for each lab member in the `/_people` directory, with name format `lastname.firstname.md` (this is just to be tidy and for alphabetic ordering when the site is built).

Add a headshot or two to the `/assets/img/` directory. Then edit the markdown file: at the top of the file there is a short yaml header between two sets of three hyphens,  which should be filled (starting with `layout: person`)

```yaml
---
layout: person
name:        # Full Name Here
position:    # see "positions" description below
description: # subtitle, such as Principal Investigator, or Associate
img:         # imagename (in the /assets/img/ directory)

profile:
  img: # imagename (in /assets/img) optional, another image for the personal page, if different from the one on the people page
  office: # address, if you want this
  cv: # link to cv
  website: # link to external personal webpage
  link: 
    url:  # url for other link (such as google scholar profile or something)
    text: # text to show for this link.

---
```
Below this, enter the person's profile/bio as markdown/html.

### Positions

The `position` attribute determines where (and whether) the person will appear on the People page.

Notes for specific `position`s:

- `faculty`: `description` should be the level, that is "Principal Investgator" or "Associate"
- `postdoc`: (not currently set up)
- `grad`:
- `undergrad`:
- `alum`: will appear in a simple list. link to website, if there is a website listed under `profile:website`.
- `assoc`: this is for associated collaborators for whom we want a profile on the site. The `description` should be the external university (such as "Mila") for students being directly advised by one of the lab members.

## Publications

The publications page is generated from .bib files located in the `_/bibliography` directory, using [jekyll-scholar](https://github.com/inukshuk/jekyll-scholar).  Options for jekyll scholar are specified in the `_config.yml` (see [jekyll-scholar](https://github.com/inukshuk/jekyll-scholar) readme for more info)  Anything in the file `default.bib` will be included, plus anything in any additional files that are specified when the bibliography is built, as in `publications.md`, for instance, where `{% bibliography --file tim.bib --file morgan.bib %}` outputs the bibliography from `default.bib` plus `tim.bib` and `morgan.bib`.

Links are automatically generated for a dropdown abstract, or link to a PDF of a paper, depending on the presence of an `abstract`, or `url` tag in the bib entry, respectively. This is specified in [_layouts/bib.html](_layouts/bib.html).

**TODO**: Currently there is an issue with urls that contain the tilde character (`~`).  This is because jekyll-scholar uses a filter for bibtex that converts certain latex syntax (using [bibtex-ruby](https://github.com/inukshuk/bibtex-ruby)) while reading the bib file, and the `~` character is replaced with a non-breaking space, which results in a broken link (`~` becoming `%C2%A0`).  This filter can be disabled, by manually setting the latex filter to not be used, in [_config.yml](_config.yml) like so

```yaml
scholar:
  bibtex_filters:
    # - latex
```

However, this breaks a lot of other nice things, mostly making a lot of curly braces show up where we don't want them.

**HACK**: Currently there is just a hack solution: within the bib files in `_/bibliography/*.bib`, manually replace all occurences of the character `~` (in a URL) with the string `\%7E` (that is, the [URL-encoding](https://en.wikipedia.org/wiki/Percent-encoding#Character_data) for the LaTex escape in HTML). 

### Putting links into bib files

By setting one of the following tags in a given bib file, links are generated in the following way, either to internal or external files:

- `url`/`html`/`preprint`/`code` `= {http://somewhere.html}` - a link to the URL `http://somewhere.html` (presumably site-external)
- `pdf`/`poster`/`slides` `= {some.pdf}` - a link to a file `some.pdf` in the `/_assets/pdfs/` folder (site internal)
- `abstract = {Some text}` - a collapsing box with the text 'Some text' in it
- `arxiv = {XXXX.YYYYY}` - a link to `http://arxiv.org/abs/XXXX.YYYYY`
- `lingbuzz = {somewhere.html}` a link to `https://ling.auf.net/lingbuzz/Something"`


For example, in the following, bib file, 
```
@article{portelance.e:2017,
  Title = {Mildly context-sensitive grammar induction and variational {B}ayesian inference},
  Author = {Portelance, Eva and Bruno, Chris and Bergen, Leon and O'Donnell, Timothy J.},
  Journal = {{arXiv}},
  Number = {arXiv:1710.11350 [cs.CL]},
  arxiv = {1710.11350},
  Year = {2017},
  abstract = {The following technical report presents a formal approach to probabilistic minimalist grammar parameter estimation. We describe a formalization of a minimalist grammar. We then present an algorithm for the application of variational Bayesian inference to this formalization.}}
```
the  `arxiv` tag generates a link to the appropriate page on arxiv.org (https://arxiv.org/abs/1710.11350), and the `abstract` tag generates a collapsing html element with the text of the abstract in it.

