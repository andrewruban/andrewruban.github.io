---
layout: post # Specifies which layout file to use (_layouts/post.html)
title:  "how2create-blog-on-jekyll"
date:   2025-04-27 10:01:00 +0000 # Optional: specific time/timezone
categories: jekyll update # Optional: categories for organization
---


## Phase 1: Prerequisites & Local Setup

##### Install Prerequisites:

- **Ruby**: Jekyll is built with Ruby. You'll need a specific version (check the Jekyll documentation for current requirements). Using a Ruby version manager like rbenv (macOS/Linux) or uru (Windows) is highly recommended to avoid conflicts with system Ruby.
- **Bundler**: This is a Ruby gem that manages your project's dependencies. Install it using Ruby's package manager, gem:

```shell
gem install bundler
```

- **Git**: You need Git to manage your code versions and push to GitHub. Download and install it from the official Git website.
- **GitHub Account**: You'll need a free account on GitHub.

##### Install Jekyll:

Once Ruby and Bundler are set up, install the jekyll gem:
```shell
gem install jekyll
```

##### Create Your Jekyll Site Locally:

- Navigate to the directory where you want to keep your blog's files using your terminal or command prompt. 
- Run the jekyll new command to create a new site scaffold. Replace my-awesome-blog with your desired local folder name:
```shell
jekyll new andrewruban
```

- Change into the newly created directory:
```shell
cd andrewruban
```

##### Understand the Basic Structure:

- `_config.yml`: Your site's main configuration file (title, description, URL, etc.).
- `_posts`: Where your blog posts (written in Markdown) will live. Filename format is crucial: `YYYY-MM-DD-your-post-title.md`.
- `_layouts`: HTML templates defining the structure of different page types (e.g., `default.html`, `post.html`).
- `_includes`: Reusable HTML snippets (like header, footer).
- `assets`: For your CSS, JavaScript, images, etc.
- `index.md` (or `index.html`): Your homepage content.
- `Gemfile`: Lists the Ruby gems (dependencies) your site needs, managed by Bundler.
- `Gemfile.lock`: Records the exact versions of gems used.

Inside your blog's directory (andrewruban), start the Jekyll development server:
```shell
bundle exec jekyll serve
```

	Why bundle exec? This ensures you're using the specific Jekyll version defined in your Gemfile, preventing potential version conflicts.

Open your web browser and go to http://127.0.0.1:4000 (or the address shown in the terminal output). You should see the default Jekyll theme site!
Leave this server running. It will automatically rebuild the site whenever you save changes to files, allowing you to preview live. Press Ctrl+C in the terminal to stop it.


## Phase 2: GitHub Repository Setup

##### Create a GitHub Repository:

- Log in to your GitHub account. 
- Create a new repository.
- Crucially, name the repository exactly 
```text
andrewruban.github.io.
```

- Replace your-github-username with your actual GitHub username. This specific naming convention tells GitHub Pages that this repository is for your user/organization site.
- Keep it Public. GitHub Pages for user sites requires the repository to be public on the free tier.
- Do NOT initialize the repository with a README, .gitignore, or license yet. You'll push your local files.

##### Initialize Git Locally & Connect to GitHub:

Initialize a Git repository:
```shell
git init -b main
git add .
git commit -m "Initial Jekyll site setup"

# https URL
git remote add origin https://github.com/your-github-username/your-github-username.github.io.git
```

Verify the remote was added:
```shell
git remote -v
```

## Phase 3: Deployment to GitHub Pages

Push Your Code to GitHub:
```shell
git push -u origin main
```

##### Enable GitHub Pages (Automatic for User Sites):

- For repositories named username.github.io, GitHub Pages is usually enabled automatically upon the first push to the main branch.
- Wait a few minutes: GitHub Pages needs time to build your Jekyll site for the first time.
- Check Deployment Status: Go to your repository on GitHub -> Settings -> Pages. You should see a message indicating your site is published at https://andrewruban.github.io . It might initially show it's building.
- Access Your Live Blog: Once built, visit https://andrewruban.github.io in your browser. You should see the same site you previewed locally!

## Phase 4: Content Creation & Customization

Write Your First Post:

Create a new file in the _posts directory. 
Remember the naming convention: YYYY-MM-DD-title-of-your-post.md.
Example: 2025-04-27-hello-world.md
Write your post content using Markdown. Start with YAML Front Matter:

```text
---
layout: post # Specifies which layout file to use (_layouts/post.html)
title:  "Hello World!"
date:   2023-10-27 10:00:00 +0000 # Optional: specific time/timezone
categories: jekyll update # Optional: categories for organization
---

Welcome to my new blog!

This is my first post written in **Markdown**.

*   It's easy!
*   It's fun!

```

Save the file.
##### Preview Locally:

If your local server (bundle exec jekyll serve) is still running, it should automatically detect the new post and rebuild. Refresh your browser at http://127.0.0.1:4000.
If the server isn't running, start it again.

##### Commit and Push Changes:

Add the new post file to Git:
```shell
git add _posts/YYYY-MM-DD-title-of-your-post.md # Use the actual filename
git commit -m "Add first blog post"
git push
```

Wait a minute or two for GitHub Pages to rebuild, then check your live site.

Customize:
- **Configuration (`_config.yml`):** Edit this file to change your blog's title, author name, description, email, social media links (depending on the theme), etc. Remember to restart the local server after changing `_config.yml`.
- **Themes:** The default theme is `minima`. You can explore and install other Jekyll themes. Check out resources like Jekyll Themes, GitHub Pages Themes, or create your own. Theme installation usually involves updating the `Gemfile` and `_config.yml`.
- **Layouts & Includes:** Modify files in `_layouts` and `_includes` (or create your own) to change the HTML structure and appearance. This requires HTML/CSS knowledge.
- **Static Pages:** Create pages like "About" or "Contact" by adding Markdown files (e.g., `about.md`) to the root directory. Add YAML front matter similar to posts (usually using the `page` layout).

**Ongoing Workflow**

1. Write/edit posts or pages locally (in `_posts` or root directory).
2. Modify configuration, layouts, or styles as needed.
3. Preview changes using `bundle exec jekyll serve`.
4. Stage changes (`git add .` or specific files).
5. Commit changes (`git commit -m "Descriptive message"`).
6. Push changes to GitHub (`git push`).
7. Wait for GitHub Pages to rebuild and check the live site.

## Adding Standard Images (Pictures)

This is the most common method for photos, screenshots, etc.

- **Create an Assets Folder:** It's best practice to keep your images organized. In the root directory of your Jekyll project (the same level as `_posts`, `_config.yml`), create a folder named `assets` if it doesn't exist. Inside `assets`, you might want to create another folder called `images`
```text
my-awesome-blog/
├── _config.yml
├── _posts/
├── assets/
│   └── images/  <-- Create this
├── ...
└── index.md
```

- **Place Your Image:** Copy your image file (e.g., `my-cool-photo.jpg`) into the `assets/images/` directory.

- **Use Markdown Syntax:** In your blog post's Markdown file (`.md`), use the standard Markdown image syntax:

```text
![Alt text describing the image](/assets/images/my-cool-photo.jpg "Optional Title Text")
```

- `![Alt text...]`: The alt text is crucial for accessibility (screen readers) and SEO. Describe the image concisely.
- `(/assets/images/my-cool-photo.jpg)`: This is the path to your image _relative to the root of your site_. Using a leading slash `/` makes the path absolute to your site's base URL, which is generally more reliable than relative paths from the post file itself.
- `"Optional Title Text"`: This text appears when a user hovers their mouse over the image in some browsers.

```text
---
layout: post
title:  "My Post with a Picture"
date:   2023-10-28 11:00:00 +0000
categories: blog images
---

Check out this cool photo I took:

![A picture of a sunset over the mountains](/assets/images/sunset-mountains.jpg "Mountain Sunset")

Isn't it neat?

```
