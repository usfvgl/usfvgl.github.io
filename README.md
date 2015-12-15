# Visualization and Graphics Lab

This is the website repository for the **Visualization and Graphics Lab (VGL)** at the [**University of San Francisco**](http://www.usfca.edu/). 

## Updates

To update the list of papers, talks, or books, edit the `papers.yml` data file. To update the list of courses, edit the `courses.yml` data file. To update the list of people (including students), edit the `people.yml` data file.

If you want to add a news post, you must place a file with the correct format in the `news/_posts` directory. The file name should be in the format:

```
yyyy-mm-dd-short-title.html
```

See one of the existing files for the required header. The content can be written in Markdown or HTML using Bootstrap classes. This is the same process for adding DVSS events (but the templates require more information).

The other files and templates only need to be modified if you are changing the style or paragraph text that appears at the start of each page.

## Setup

Github Pages uses an [older version](https://pages.github.com/versions/) of `jekyll`, so I recommend you follow the steps at:

<https://help.github.com/articles/using-jekyll-with-pages/>

Once installed, you can generate the site locally with:

```
bundle exec jekyll serve --watch
```

## Notes

Currently, the formatting of the HTML output is prioritized over the formatting of the template code. This results in more difficult to read template code, but the public facing HTML output should be semi-decent. Indentation is an issue since some text/templates appear on multiple pages, so for the most part the HTML code uses very little indentation.

A balance between both might be reachable once Github Pages upgrades to newer versions of its dependencies.