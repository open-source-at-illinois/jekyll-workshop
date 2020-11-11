
## Exercise 3.1: Using layouts to wrap your text content

Readings:
- [Part 4](https://jekyllrb.com/docs/step-by-step/04-layouts/)

Objectives:
- Understand how to implement Jekyll layouts

So far, you've been writing content in YAML files. Is this all there is to Jekyll? Writing content vicariously through YAML, and writing Liquid all day long? Nope! 

One of the great things of Jekyll is that you can write in Markdown. If you've ever made posts on Reddit, StackOverflow, Discord, or even Piazza, you know a little bit about how Markdown works.

That being said, let's get into it!

Just a recap on layouts: layouts are special templates from which Jekyll makes new pages. They are stored in the special directory `_layouts`.

First, convert your `index.html` so that it's the "default" layout. Be sure to read [Part 4](https://jekyllrb.com/docs/step-by-step/04-layouts/) to understand how to make Jekyll recognize the HTML file as a layout. We want the "content" to be wrapped inside a `<div>` element.

Then, create a file `index.md`. After Jekyll parses it, it will be generated as `index.html` and Jekyll will convert all Markdown to HTML. 

This is what we are working towards:

![](exercise3-1-goal.png)

And this is what we want `index.md` to look like in the end:

### /index.md

```md
---
layout: default
classes:
    - name: ECE 120
      rating: 3
      difficulty: 2
      remarks: LC3 is cool, I guess, but I thought I was going to build the next Linux
      warnings: Do your homework, folks.
    - name: MATH 214
      rating: 2
      difficulty: 5
      remarks: 3 integrals 5 me
    - name: CS 225
      rating: 4
      difficulty: 4
      remarks: Data structures are easy, Git is hard and I keep forgetting to push before the deadline

---

<hr/>
### Disclaimer

But these are just, like, my opinions. Pls don't sue. 
```

(Sidenote: Mixing HTML and Markdown is a-okay -- Jekyll will do a pass on the file to convert all Markdown to HTML later anyway.)
To test, run `jekyll serve`, or if that's not working, run `bundle exec jekyll serve`. When you're good, read on.


## Exercise 3.2: Layouts on layouts???

Readings:
- [Part 4](https://jekyllrb.com/docs/step-by-step/04-layouts/)

Objectives:
- Understand how to reuse encapsulating HTML by layering layouts

Yes, that's right! You're able to create layouts based on other layouts. This is good when you want to reuse encapsulating aspects of your page.

What if our page detailing tips on how to survive UIUC classes goes viral, and people want to know what glorious individual came up with these tips? We need an About page!

But hold on...the code for our ratings system is in the `default` layout. That means that we'd get a bunch of text and HTML that's really not useful for an About page (that's meant for putting class ratings). But we still want to reuse the title of the page, and maybe a footer with our social media (when we refactor), and anything else that we might want to surround our content! What do we do?!?!?!

The solution is straightforward: we split our current layout into two layouts:
- `_layouts/default.html`, which will ONLY have the required meta-HTML tags (like `<head>`, `<!DOCTYPE>`), and the title of our page (in the `<h1>` tag)
- `_layouts/ratings.html`, which will have all the Liquid and code that we wrote in Exercise 2.

You can do this by...you guessed it, putting `layout: default` in the front matter of `_layouts/ratings.html`!

After you've successfully refactoring our initial layout as two separate layouts, create an `about.md` page at the root of your project directory, with this content (or something similar):

### /about.md
```
---
layout: default
---

## About Me

My name is Linus OpenSourceMan, and I'm a student at the University of Illinois at Urbana-Champaign. I really like pumpkins, but I love open source more!

```

Your `index.md` should look the exact same, EXCEPT for the fact that it has `layout: ratings` instead of `layout: default`. The actual `index.html` page when you test it should look the same as it did last time.

Your `about.html` page should look something like this:

![](./exercise3-2-goal.png)

By the end, this is what your directory structure should look like:

```
.
├── about.md
├── Gemfile
├── Gemfile.lock
├── index.md
└── _layouts
    ├── default.html
    └── ratings.html
```

To test your `index.html`, run `jekyll serve`, or if that's not working, run `bundle exec jekyll serve`. 
To test your `about.html`, run the above commands and then navigate to `http://127.0.0.1:4000/about.html`.

When you're good, read on.