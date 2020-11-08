# Jekyll Workshop

Hello everybody! Welcome to the Jekyll workshop by OSAI.

You'll be going through the Jekyll step-by-step tutorial [here](https://jekyllrb.com/docs/step-by-step/01-setup/), but we'll provide a different set of exercises for you to do in order to get comfortable with Jekyll. :D

In this workshop, you'll be creating a Jekyll site to detail your tips for surviving your UIUC classes! 

So, that being said, whenever you see the page tell you to *do* something, we recommend you follow **our** step-by-step tutorial (you can also do their tutorial if you want -- it's a free country). Their tutorial is great, but it's a little lacking in giving you the experience of actually *writing* Jekyll pages.


## Important Notes
1.) We're using "Linus" as a dummy name to put. Do put your own name instead :)
2.) This tutorial is harder than the default tutorial, but it should give you a better understanding of what Jekyll is. If you have any questions, send a message in the Discord and @Sahan!
3.) If you have any improvements or suggestions to make, please make a PR to this repo, or open an issue. We'd love to use this workshop for future years in the club, so we want this to be as useful as possible!


## Exercise 1: Setup

Objectives:
- Set up Ruby and Jekyll on your own computer.
- Learn how to run a local development build of Jekyll and test your page.

Readings: 
- [Part 1](https://jekyllrb.com/docs/step-by-step/01-setup/)

Go through the procedure in Part 1 to initialize jekyll in your project. After that, create `index.html` in the root of your project such that it has "Linus's UIUC Survival Guide" as an `h1` element, and the title is "Linus UIUC Tips":

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

To test, run `jekyll serve`, or if that's not working, run `bundle exec jekyll serve`. When you're good, keep going on.

## Exercise 2: Liquid and Front Matter

Objectives:
- Learn how YAML and Liquid come together in Jekyll pages.
- Learn how to make use of Liquid tags, filters, and objects.

Readings: 
- [Part 2](https://jekyllrb.com/docs/step-by-step/02-liquid/)
- [Part 3](https://jekyllrb.com/docs/step-by-step/03-front-matter/)
- [YAML 101](https://gutsytechster.wordpress.com/2019/03/21/yaml-101/) up to and including "Multi-line Strings" if you aren't familiar with YAML. 


Now that you've read both Part 2 and Part 3, you'll be writing some HTML and Liquid in order to write each of your classes and write some notes on them! Here's the format you'll implement:

```yaml
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
```

![](exercise2-goal.png)

If the above picture is ambiguous, here is what you need to implement:

- For each class, 
  - (Exercise 2.1) Print out the name as an `<h2>` element.
  - (Exercise 2.2) Print out the rating and then `/ 5` after it as a `<p>` element
  - (Exercise 2.3) If the difficulty is a `5`, print out `WARNING` and then print out the difficulty (and then optionally, a `/ 5` after it). Otherwise, just print the difficulty (and the optional `/ 5`). All of this is in a `<p>` element.
  - (Exercise 2.4) Print out the remarks for the class in a `<p>` element.
  - (Exercise 2.5) If there are warnings, print out the warnings for the class in a `<p>` element, but make sure it's all uppercase.


This might take you some time to do. If you're struggling with figuring out the Liquid, [here](https://shopify.dev/docs/themes/liquid/reference/) is the official reference. It is a quite good reference. Alternatively, feel free to Google whatever you need in order to do this (example searches: "how to loop in Jekyll", "how to uppercase text in Jekyll", etc.).

To test, run `jekyll serve`, or if that's not working, run `bundle exec jekyll serve`. When you're good, read on.

### Some final remarks

Jekyll is very good for static pages that have structured data. So, a good plan for making Jekyll pages is: 

1) Figure out the structure of your data first
2) Figure out how the page will look like
3) Write the HTML/CSS/Liquid for it.

## Exercise 3.1: Using layouts to wrap your text content

Readings:
- [Part 4](https://jekyllrb.com/docs/step-by-step/04-layouts/)

Objectives:
- Understand how to implement Jekyll layouts

So far, you've been writing content in YAML files. Is this all there is to Jekyll? Writing content vicariously through YAML, and writing Liquid all day long? Nope! 

One of the great things of Jekyll is that you can write in Markdown. If you've ever made posts on Reddit, StackOverflow, Discord, or even Piazza, you know a little bit about how Markdown works.

That being said, let's get into it!

First, convert your `index.html` so that it's the "default" layout. Be sure to read [Part 4](https://jekyllrb.com/docs/step-by-step/04-layouts/) to understand how to make Jekyll recognize the HTML file as a layout. We want the "content" to be wrapped inside a `<div>` element.

Then, create a file `index.md`. After Jekyll parses it, it will be generated as `index.html` and Jekyll will convert all Markdown to HTML. 

This is what we are working towards:

![](exercise3-1-goal.png)

And this is what we want `index.md` to look like in the end:

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

To test your `index.html`, run `jekyll serve`, or if that's not working, run `bundle exec jekyll serve`. 
To test your `about.html`, run the above commands and then navigate to `http://127.0.0.1:4000/about.html`.


When you're good, read on.
