# Nacho Dog Blog

Lives at https://nacho.dog/blog/. Plain HTML, no build step: push to `main` and GitHub Pages deploys it.

## Writing a new post
1. Copy `posts/_template.html` to `posts/your-post-name.html` and fill in the title, date, tags and body.
2. Put images in `img/` and reference them as `../img/photo.jpg`. Resize big phone photos first (~1600px wide is plenty).
3. Add a `<li>` at the top of the "All posts" list in `index.html` (and a project card if you want it featured).
4. Optionally link the new post from the previous post's "next" link at the bottom.

## Finishing the starter posts
Each starter post has dashed "TO DO" boxes (`<div class="todo">…</div>`). Replace each one with your own text, images or video, then delete the box.

Styles for every page are in `blog.css`.
