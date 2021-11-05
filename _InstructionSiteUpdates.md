# Editing website content and layout

The Hackweek website is a Jekyll site that uses the [Jekyll Spectral theme.](http://jekyllthemes.org/themes/spectral/)

## Location of main content documents

Relevant, editable content is organized in the following directories and files:

- [_config.yml](https://github.com/ICESAT-2HackWeek/icesat-2hackweek.github.io/blob/source/_config.yml): core Jekyll site configuration, including some banner/header/footer text and urls
- [jekyll-spectral-theme/_includes](https://github.com/ICESAT-2HackWeek/icesat-2hackweek.github.io/tree/source/jekyll-spectral-theme/_includes) directory: front page content, broken up into sections, one markdown file per section.
  - The layout templates for sections and section order are controlled by [jekyll-spectral-theme/_layouts/default.html](https://github.com/ICESAT-2HackWeek/icesat-2hackweek.github.io/blob/source/jekyll-spectral-theme/_layouts/default.html)
  - Each section specifies a template for its layout, where the templates available are found in [jekyll-spectral-theme/_layouts](https://github.com/ICESAT-2HackWeek/icesat-2hackweek.github.io/tree/source/jekyll-spectral-theme/_layouts)
  - Section two ("Information for Applicants") is a special beast. While [jekyll-spectral-theme/_includes/pages.html](https://github.com/ICESAT-2HackWeek/icesat-2hackweek.github.ioo/blob/source/jekyll-spectral-theme/_includes/pages.html) orchestrates it, the directives there point to content to be grabbed from tags `title` and `description` in [_pages/01-applicants.md](https://github.com/ICESAT-2HackWeek/icesat-2hackweek.github.io/blob/source/_pages/01-applicants.md)
- [_pages](https://github.com/ICESAT-2HackWeek/icesat-2hackweek.github.io/tree/source/_pages): content for extra pages, including all the pages accessible via the drop-down menu on the upper right of the page.
  - The destination page file name (what a user sees) is *not* the source markdown file name on the repository; instead, the destination file name is found in the `permalink` tag within the markdown file. For example, for [_pages/01-applicants.md](https://github.com/ICESAT-2HackWeek/icesat-2hackweek.github.io/blob/source/_pages/01-applicants.md), the destination file name is [applicant-info.html](https://icesat-2hackweek.github.io/applicant-info.html)

Note that apparently any Markdown file dropped at the root level of the repository, or in the `_pages` directory (or possibly anywhere else?), will be automatically added to the Menu drop down; except ones with names starting with the `_` character.

## Editing and testing locally (in your computer) with Jekyll

Clone the GitHub repo locally, then edit the content of files following the documentation in the previous section. To view your changes, rebuild the site using Jekyll.

Install Ruby and Jekyll locally through conda.
The recommended approach is:

```shell
conda create --name JEKYLL -c conda-forge rb-bundler compilers
conda activate JEKYLL
bundle install
```

However, this may not work for some MacOS users.
In that case, use (exactly as written - you cannot combine the conda install steps):
```shell
conda create --name JEKYLL -c conda-forge ruby
conda activate JEKYLL
conda install -c conda-forge clangxx_osx-64
gem install bundler
bundle install
```

To build and serve the site (all OS), run this statement:

```shell
bundle exec jekyll serve
```

The site will be available at `http://127.0.0.1:4000/`.

