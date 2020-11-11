## Exercise 1: Setup

Objectives:
- Set up Ruby and Jekyll on your own computer.
- Learn how to run a local development build of Jekyll and test your page.

Readings: 
- [Part 1](https://jekyllrb.com/docs/step-by-step/01-setup/)

Go through the procedure in Part 1 to initialize jekyll in your project. After that, create `index.html` in the root of your project such that it has "Linus's UIUC Survival Guide" as an `h1` element, and the title is "Linus UIUC Tips":

### /index.html
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Linus UIUC Tips</title>
  </head>
  <body>
    <h1>Linus's UIUC Survival Guide</h1>
  </body>
</html>
```

By the end of it, your file structure should look like this:

```
.
├── Gemfile
├── Gemfile.lock
├── index.html
└── _site
    └── index.html
```

To test, run `jekyll serve`, or if that's not working, run `bundle exec jekyll serve`. Notice that every time you make a change in the source files in your Jekyll project, Jekyll will automatically refresh with the new content. This it really easy to see what changes you've made. When you've got Jekyll working, move on to the next exercise.

Clarification: when you go to a certain URL on the web, like google.com, what you'll first see is the contents of `index.html` under that URL. So that's why us changing our `index.html` has the consequences we see!