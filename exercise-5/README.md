## Exercise 5: GitHub Deployment!

Reading:
- [Jekyll GitHub Pages Documentation](https://jekyllrb.com/docs/github-pages/)

Phew, you've finally made it to the end! All that's left for you to do is to put your website on GitHub Pages.
So, step 0 would be to create a `.gitignore` to make sure we don't commit any of Jekyll's build files:

### /.gitignore
```
_site/
.sass-cache/
.jekyll-cache/
.jekyll-metadata
```

Step 1 would be to follow the instructions in the reading to make your Jekyll project compatible with GitHub (by adding the "github-pages" gem and by putting the `relative_url` filter where necessary).

Step 2 would then to be initialize a git repository in the root of the project, add everything with `git add .` and commit everything with `git commit -m "Initial commit"`, and then create a GitHub repo on your account and push your Jekyll project to GitHub.

After that, follow the instructions [here](https://forestry.io/docs/guides/hosting/github-pages-jekyll/) to get your pages up and running. And then you're done!


## What's next?

Well, as you can see, the page you have now is missing a few things. For example,

* There's no navigation mechanism to get from one page to another, except for going into posts.
* Only raw HTML is being rendered -- there's no styling at all.
* There are plenty of cool little plugins to use for Jekyll, like an RSS plugin.

And more! You can either fix up this workshop project and make it your own, or you can start anew with a Jekyll template and start modifying it to your heart's content. Example: https://github.com/jekyll/minima. (Fun fact, https://open-source-at-illinois.github.io/workshops/ is based off of this theme!)

You can also start exploring Jekyll Themes to use for your next blogging project/documentation-like project. Though it might seem like everything costs money, there are a good number of polished, free Jekyll templates to use.

That's it. Have fun!