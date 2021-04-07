# Argument Parser
[heading__top]:
  #includes-font
  "&#x2B06; Builds link elements for loading fonts in a respectful fashion"


Builds link elements for loading fonts in a respectful fashion


## [![Byte size of Argument Parser][badge__main__includes_font__source_code]][includes_font__main__source_code] [![Open Issues][badge__issues__includes_font]][issues__includes_font] [![Open Pull Requests][badge__pull_requests__includes_font]][pull_requests__includes_font] [![Latest commits][badge__commits__includes_font__main]][commits__includes_font__main]


---


- [:arrow_up: Top of Document][heading__top]

- [:building_construction: Requirements][heading__requirements]

- [:zap: Quick Start][heading__quick_start]
  - [:memo: Edit Your ReadMe File][heading__your_readme_file]
  - [:floppy_disk: Commit and Push][heading__commit_and_push]

- [&#x1F9F0; Usage][heading__usage]
  - [Example YAML/FrontMatter][heading__example_yamlfrontmatter]
  - [:fountain: Example Layout][heading__example_layout]
  - [:spider_web: Example Output][heading__example_output]

- [&#x1F523; API][heading__api]
  - [`include.href`][heading__includehref]
  - [`include.preconnect`][heading__includepreconnect]
  - [`include.filter`][heading__includefilter]

- [&#x1F5D2; Notes][heading__notes]

- [:chart_with_upwards_trend: Contributing][heading__contributing]
  - [:trident: Forking][heading__forking]
  - [:currency_exchange: Sponsor][heading__sponsor]

- [:card_index: Attribution][heading__attribution]

- [:balance_scale: Licensing][heading__license]


---



## Requirements
[heading__requirements]:
  #requirements
  "&#x1F3D7; Prerequisites and/or dependencies that this project needs to function properly"


This repository depends upon [Jekyll][jekyll_rb__home] which is supported by [GitHub Pages][github_docs__github_pages__jekyll], further details about setup can be found from [documentation][jekyll_rb__github_pages] published by the Jekyll maintainers regarding GitHub Pages.


______


## Quick Start
[heading__quick_start]:
  #quick-start
  "&#9889; Perhaps as easy as one, 2.0,..."


This repository encourages the use of Git Submodules to track dependencies


**Bash Variables**


```Bash
_module_name='includes-font'
_module_https_url="https://github.com/liquid-utilities/includes-font.git"
_module_base_dir='_layouts/modules'
_module_path="${_module_base_dir}/${_module_name}"
```


**Bash Submodule Commands**


```Bash
cd "<your-git-project-path>"

git checkout gh-pages
mkdir -vp "${_module_base_dir}"

git submodule add\
 -b main --name "${_module_name}"\
 "${_module_https_url}" "${_module_path}"
```


---


### Your ReadMe File
[heading__your_readme_file]:
  #your-readme-file
  "&#x1F4DD; Suggested additions for your ReadMe.md file so everyone has a good time with submodules"


Suggested additions for your _`ReadMe.md`_ file so everyone has a good time with submodules


```MarkDown
Clone with the following to avoid incomplete downloads


    git clone --recurse-submodules <url-for-your-project>


Update/upgrade submodules via


    git submodule update --init --merge --recursive
```


### Commit and Push
[heading__commit_and_push]:
  #commit-and-push
  "&#x1F4BE; It may be just this easy..."


```Bash
git add .gitmodules
git add "${_module_path}"


## Add any changed files too


git commit -F- <<'EOF'
:heavy_plus_sign: Adds `liquid-utilities/includes-font#1` submodule



**Additions**


- `.gitmodules`, tracks submodules AKA Git within Git _fanciness_

- `README.md`, updates installation and updating guidance

- `_modules_/includes-font`, Builds link elements for loading fonts in a respectful fashion
EOF


git push origin gh-pages
```


**:tada: Excellent :tada:** your project is now ready to begin unitizing code from this repository!


______


## Usage
[heading__usage]:
  #usage
  "&#x1F9F0; How to utilize this repository"


How to utilize this repository


---


### Example YAML/FrontMatter
[heading__example_yamlfrontmatter]: #example-yamlfrontmatter


```yaml
fonts_list:
  - href: assets/fonts/custom-font.css
    preconnect: /
    filter: relative_url

  - href: https://fonts.googleapis.com/css2?family=Merriweather&display=swap
    preconnect: https://fonts.gstatic.com
```


---


### Example Layout
[heading__example_layout]:
  #example-layout
  "&#x26F2;"


**`page.html` (snip)**


```liquid
<!DOCTYPE html>
<html lang="en">
  <head>
    {% assign fonts_list = page.fonts_list
                         | default: site.fonts_list
                         | default: layout.fonts_list %}

    {%- for font in fonts_list -%}
      {% include _includes/modules/include-font/font.html
                 href=font.href
                 preconnect=font.preconnect
                 filter=font.filter %}
    {%- endfor -%}
  </head>
</html>
```


---


### Example Output
[heading__example_output]:
  #example-output
  "&#x1F578;"


```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <link rel="preconnect"
          href="/project-name"/>

    <link rel="preload"
          as="style"
          href="/project-name/assets/fonts/custom-font.css"/>

    <link rel="stylesheet"
          href="/project-name/assets/fonts/custom-font.css"
          media="print"
          onload="this.media='all'"/>

    <noscript>
      <link rel="stylesheet"
            href="/project-name/assets/fonts/custom-font.css"/>
    </noscript>


    <link rel="preconnect"
          href="https://fonts.gstatic.com"
          crossorigin/>

    <link rel="preload"
          as="style"
          href="https://fonts.googleapis.com/css2?family=Merriweather&display=swap"/>

    <link rel="stylesheet"
          href="https://fonts.googleapis.com/css2?family=Merriweather&display=swap"
          media="print"
          onload="this.media='all'"/>

    <noscript>
      <link rel="stylesheet"
            href="https://fonts.googleapis.com/css2?family=Merriweather&display=swap"/>
    </noscript>
  </head>
</html>
```

______


## API
[heading__api]:
  #api
  "&#x1F523; Documentation for classes, methods, parameters, and custom types/data-structures"


Documentation for classes, methods, parameters, and custom types/data-structures


---


### `include.href`
[heading__includehref]:
  #includehref
  "Required, path or URL to font CSS configurations"


Required, path or URL to font CSS configurations


**Remote Example**


```
https://fonts.googleapis.com/css2?family=Merriweather&display=swap
```


**Self Hosted Example**


```
/project-name/assets/fonts/custom-font.css
```


---


### `include.preconnect`
[heading__includepreconnect]:
  #includepreconnect
  "Recommend, domain or root path of site hosting CSS font configurations"


Recommend, domain or root path of site hosting CSS font configurations


**Remote Example**


```
https://fonts.googleapis.com/
```


**Self Hosted Example**


```
/project-name/
```


---


### `include.filter`
[heading__includefilter]:
  #includefilter
  "Optional, useful for self hosted CSS font configurations"


Optional, may be `absolute_url` or `relative_url`, useful for self hosted CSS font configurations.


> Note, when **not** defined `crossorigin` is inserted within `link` using `preconnect`


______


## Notes
[heading__notes]:
  #notes
  "&#x1F5D2; Additional things to keep in mind when developing"


This repository may not be feature complete and/or fully functional, Pull Requests that add features or fix bugs are certainly welcomed.


______


## Contributing
[heading__contributing]:
  #contributing
  "&#x1F4C8; Options for contributing to includes-font and liquid-utilities"


Options for contributing to includes-font and liquid-utilities


---


### Forking
[heading__forking]:
  #forking
  "&#x1F531; Tips for forking includes-font"


Start making a [Fork][includes_font__fork_it] of this repository to an account that you have write permissions for.


- Add remote for fork URL. The URL syntax is _`git@github.com:<NAME>/<REPO>.git`_...


```Bash
cd ~/git/hub/liquid-utilities/includes-font

git remote add fork git@github.com:<NAME>/includes-font.git
```


- Commit your changes and push to your fork, eg. to fix an issue...


```Bash
cd ~/git/hub/liquid-utilities/includes-font


git commit -F- <<'EOF'
:bug: Fixes #42 Issue


**Edits**


- `<SCRIPT-NAME>` script, fixes some bug reported in issue
EOF


git push fork main
```


> Note, the `-u` option may be used to set `fork` as the default remote, eg. _`git push -u fork main`_ however, this will also default the `fork` remote for pulling from too! Meaning that pulling updates from `origin` must be done explicitly, eg. _`git pull origin main`_


- Then on GitHub submit a Pull Request through the Web-UI, the URL syntax is _`https://github.com/<NAME>/<REPO>/pull/new/<BRANCH>`_


> Note; to decrease the chances of your Pull Request needing modifications before being accepted, please check the [dot-github](https://github.com/liquid-utilities/.github) repository for detailed contributing guidelines.


---


### Sponsor
  [heading__sponsor]:
  #sponsor
  "&#x1F4B1; Methods for financially supporting liquid-utilities that maintains includes-font"


Thanks for even considering it!


Via Liberapay you may <sub>[![sponsor__shields_io__liberapay]][sponsor__link__liberapay]</sub> on a repeating basis.


Regardless of if you're able to financially support projects such as includes-font that liquid-utilities maintains, please consider sharing projects that are useful with others, because one of the goals of maintaining Open Source repositories is to provide value to the community.


______


## Attribution
[heading__attribution]:
  #attribution
  "&#x1F4C7; Resources that where helpful in building this project so far."


- [CSS Tricks -- How to Load Fonts in a Way That Fights FOUT and Makes Lighthouse Happy](https://css-tricks.com/how-to-load-fonts-in-a-way-that-fights-fout-and-makes-lighthouse-happy/)

- [GitHub -- `github-utilities/make-readme`](https://github.com/github-utilities/make-readme)

- [MDN -- HTML attribute: crossorigin](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/crossorigin)


______


## License
[heading__license]:
  #license
  "&#x2696; Legal side of Open Source"


```
Builds link elements for loading fonts in a respectful fashion
Copyright (C) 2021 S0AndS0

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, version 3 of the License.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
```


For further details review full length version of [AGPL-3.0][branch__current__license] License.



[branch__current__license]:
  /LICENSE
  "&#x2696; Full length version of AGPL-3.0 License"


[badge__commits__includes_font__main]:
  https://img.shields.io/github/last-commit/liquid-utilities/includes-font/main.svg

[commits__includes_font__main]:
  https://github.com/liquid-utilities/includes-font/commits/main
  "&#x1F4DD; History of changes on this branch"


[includes_font__community]:
  https://github.com/liquid-utilities/includes-font/community
  "&#x1F331; Dedicated to functioning code"

[includes_font__gh_pages]:
  https://github.com/liquid-utilities/includes-font/tree/
  "Source code examples hosted thanks to GitHub Pages!"

[badge__gh_pages__includes_font]:
  https://img.shields.io/website/https/liquid-utilities.github.io/includes-font/index.html.svg?down_color=darkorange&down_message=Offline&label=Demo&logo=Demo%20Site&up_color=success&up_message=Online

[gh_pages__includes_font]:
  https://liquid-utilities.github.io/includes-font/index.html
  "&#x1F52C; Check the example collection tests"

[issues__includes_font]:
  https://github.com/liquid-utilities/includes-font/issues
  "&#x2622; Search for and _bump_ existing issues or open new issues for project maintainer to address."

[includes_font__fork_it]:
  https://github.com/liquid-utilities/includes-font/
  "&#x1F531; Fork it!"

[pull_requests__includes_font]:
  https://github.com/liquid-utilities/includes-font/pulls
  "&#x1F3D7; Pull Request friendly, though please check the Community guidelines"

[includes_font__main__source_code]:
  https://github.com/liquid-utilities/includes-font/
  "&#x2328; Project source!"

[badge__issues__includes_font]:
  https://img.shields.io/github/issues/liquid-utilities/includes-font.svg

[badge__pull_requests__includes_font]:
  https://img.shields.io/github/issues-pr/liquid-utilities/includes-font.svg

[badge__main__includes_font__source_code]:
  https://img.shields.io/github/repo-size/liquid-utilities/includes-font


[jekyll_rb__home]:
  https://jekyllrb.com/
  "Jekyll home page"

[jekyll_rb__github_pages]:
  https://jekyllrb.com/docs/github-pages/
  "Jekyll documentation for GitHub Pages setup"

[github_docs__github_pages__jekyll]:
  https://docs.github.com/en/github/working-with-github-pages/setting-up-a-github-pages-site-with-jekyll
  "GitHub Pages documentation on Jekyll setup"


[sponsor__shields_io__liberapay]:
  https://img.shields.io/static/v1?logo=liberapay&label=Sponsor&message=liquid-utilities

[sponsor__link__liberapay]:
  https://liberapay.com/liquid-utilities
  "&#x1F4B1; Sponsor developments and projects that liquid-utilities maintains via Liberapay"

