Groove Ultimate
==============

Herp. Derp. http://grooveultimate.com.

So you'd like to contribute?
===========================

That's rad. If you know how GitHub works and how to code, see instructions below. If you don't know how to code and/or have no idea how GitHub works, submit any copy changes/ideas/suggestions/what-have-you to groovecaptains@gmail.com, or...

Have an idea or found a bug?
-----------------------------

[Submit an issue](https://github.com/ultimatedelman/grooveultimate/issues)! It's easy as 1, 2, 3, 4, 5:

1. If you're on the website, click on the link that takes you here (the little cat-looking thing next to the Twitter and email icons in the sidebar). If you're already here...
2. On the right-hand side of this page, click the ["Issues"](https://github.com/ultimatedelman/grooveultimate/issues) link under the "Code" link.
3. Do a quick check to make sure what you're about to suggest or report hasn't already been suggested or reported. If it has, comment on the existing issue. Saying that you're having the same problem (or think the same idea is awesome!) is valuable info.
3. Click the big green button that says "New Issue".
4. Describe idea and submit!

Doing this keeps everything centrally located and easy to find and discuss without polluting anyone's email.

Directions for the coding-inclined
================================== 

For **simple** copy or HTML changes, do the following:

1. Create a fork of the `master` branch of this repo. This is where all the source files live.
2. Make your changes. [Want to create a new post?](#creating-a-new-post).
3. Submit a [pull request](https://github.com/ultimatedelman/grooveultimate/compare).

If everything checks out, I'll merge your changes and build the site.

**For more complex changes**, such as adding or modifying bios, adding pages, or [creating or modifying posts](#creating-a-new-post) where you'd like to see what it looks like locally:

1. This is a statically-generated site a la [Jekyll](http://jekyllrb.com/). If you haven't installed that, do that first.
2. Do step one for simple changes if you haven't already.
3. Set up [your server](http://jekyllrb.com/), run `jekyll serve` in your terminal/console.
5. Make your changes.
6. In your terminal/console, run `jekyll build`. You should be able to view your changes locally.
7. Repeat previous two steps until you've achieved the desired result.
8. Submit a [pull request](https://github.com/ultimatedelman/grooveultimate/compare).

Modifying CSS
=======================

This site uses the pre-compiler [Compass](http://www.compass-style.org) (SASS/SCSS) to compile its CSS. If you want to modify CSS, do the following: 

0. If you don't have Compass installed, you must run `gem install compass` from your terminal/console. Also run `gem install uglifier` and `gem install smusher`.
1. Navigate your terminal/console to `/_frontend` and run `compass watch`. Make sure there are no errors. It should say something like `Compass is polling for changes` if you did it right.
1. The source files for the CSS are the `.scss` files found in the `_frontend/src/partials` folder. Modifying the `.css` file in the `public/css` file is pointless as it is overwritten every time a change is made.
2. After you make your change and save your file, you should see your terminal automatically compile your changes. Depending on what you're modifying, it's possible that you could generate compilation errors if you save things in the wrong order. For instance, if you create a variable in one file and use it in another, but save them in backwards order, it may cause an error. Just add a space to any file and save it to trigger a recompilation.

Modifying JS
=====================

No JS yet. Will update when necessary. Similar to above instructions; Compass minifies all JS on save.

Creating a New Post
=======================

1. Create a new file in the `_posts` directory. The filename must be of the convention: `yyyy-mm-dd-title.markdown`. For example, `2014-07-25-new-post.markdown`.
2. The top of your post must have ["front-matter"](http://jekyllrb.com/docs/frontmatter/) that looks something like this: 
<pre><code>---
layout: post
title: New Website!
date: 2014-07-25 00:00:00
---</pre></code>
3. The only thing above that must remain consistent is `layout: post`. Change the values of `title` and `date` accordingly.
4. Put your content below the second `---` in [Markdown](http://daringfireball.net/projects/markdown/syntax) format. If you don't want to deal with learning Markdown syntax, don't worry about it. Type as normal and hit enter twice between paragraphs.
5. If you want to see how it looks, follow the steps for complex changes above. Otherwise, just submit a pull request.

Roster/Bios
===========

The roster and bios are dynamically generated via data in the `_data/players.yml` file. To update an existing player's roster data and/or bio, modify their entry in this file and run a `jekyll build`.

To add a new player to the roster:

1. Players are arranged alphabetically according to last name. Find their spot.
2. Enter their data in the following format (these are mandatory):
<pre><code>- name: 		  First Last
    sex: 			  f  (m for dudes)
    number: 		0
    lastYear: 	2014 (this is the last year they were on the team)
    years:      2014 (TODO: this should probably become an array)</code></pre>
3. Optional properties are:
  - `bio` - Content to appear in player's bio. Markdown is supported.
  - `facts` - Array of bullet points to list after bio, formatted like: `["Position: cutter", "Favorite food: nachos"]`
  - `isCaptain` - only put in if player is the captain, value is `true`
  - `isPractice` - only put in if player is a practice player, value is `true`
  - `isCoach` - only put in for those foolish enough to coach us, value is `true`
  - `pic` - only put in if player has a pic, value is `true`
4. To add a picture to a bio:
  1. Add the `pic` property to the player's data
  2. Make sure the image is no wider than `200px` and not absurdly tall, and has a `.jpg` file extension.
  3. Drop the image in the `assets/biopics` folder with the naming convention of `firstname-lastname.jpg` as listed in the `name` property in their data file, for instance, `sam-applegate.jpg`. If she were to change her name to how she used to refer to herself when she was a child, you'd change the `name` property to `Widdle Samamfa Applegate` and subsequently the picture to `widdle-samamfa-applegate.jpg`.
  4. Don't forget to add and commit the image to the `master` branch of the repository.
5. After you're done adding or updating data, you must run `jekyll build` to regenerate the site.

Here Be Dragons
======================
This section is more documentation for me on deployment in case I forget. We use [generators](http://jekyllrb.com/docs/plugins/#generators) on our site (way easier to generate bios dynamically and automatically than maintain them by hand). However, GitHub [doesn't support](http://jekyllrb.com/docs/plugins/) generators in their standard hosting, so the site must be built and the generated files must be pushed to the `gh-pages` branch. 

Hence, to deploy:

1. In `master` branch, run `jekyll build`. You don't have to commit afterwards, as this action does not affect any source files.
2. Switch to `gh-pages` branch. You should see all the source files disappear from the folder structure.
3. Copy or cut the files from the `_site` directory that should have survived the branch switch and paste them to the root. You can either delete or overwrite all existing files.
4. Commit, push while still in `gh-pages` branch.
5. View changes on [the site](http://grooveultimate.com).

If you are smarter than me and know of a better way to automate this deployment process, please feel free to contribute!

TODO
===========
If you are looking for other ways to contribute, there are plenty of things to do. In no particular order:

- Update the design
- Figure out the best way to do dynamic rostering per year
- Preserve old rosters
- Add any new features to the site, such as image galleries
