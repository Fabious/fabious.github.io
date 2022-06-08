---
title: 'Generate Date Front Matter'
date: 2022-06-07T21:42:17+02:00
draft: true
---

# Generate and insert date in Front Matter

While learning to write a technical blog, I stumbled upon a little problem:
I want my posts to be dated, i want the creation and the editing date. Simple, right? Right!? (insert starwars meme)

Not so simple because i don't know how to do it! Even the littlest problem can take you in a rabbit hole.

## Here is my process to fix this

Hopefully hugo generate the date automatically when you create a post with the CLI command `hugo new posts/my-new-post.md`, so i know the date format needed (for this post: `2022-06-07T21:42:17+02:00`)

Now searching in [hugo documenation](https://gohugo.io/content-management/front-matter/), `lastmod` is the variable for the editing date in Front Matter.

### The interesting part

Now how to generate this date automatically?

First i searched in the shell and the command `date`, i'm so bad with dates I don't even know what format is `2022-06-07T21:42:17+02:00` exactly...
So this is `ISO 8601` format, and I found in Stack Overflow that the command to generate it beautifully is `date -Is` (still searching how could i found this myself, especially the `s` in the flag)

To finish, a bit of vim magic with this command to insert it `:r!date -Is`, voilà!

At the time of writing vscode with vim plugin kind of crash when you try it...
