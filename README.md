# Student Blog Template

This repository is a template for students to create and deploy their own blog using Markdown files.

## Creating a Blog Post
1. Open the `/posts` folder.
1. Copy `_template.md`
1. Rename your copy (example: `2026-02-14-first-blog.md`)
1. Edit the front matter at the top:
    - title
    - date
    - summary (optional)
    - tags (optional)
1. Write your blog post underneath in markdown
1. [Commit](https://docs.github.com/en/desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project-in-github-desktop) and [push](https://docs.github.com/en/desktop/making-changes-in-a-branch/pushing-changes-to-github-from-github-desktop) your changes to the `main` branch.

Your blog will automatically update and publish online.

Your site will be available at: `https://<your-github-username>.github.io/<repository-name>`.

### Professional Tip
Your blog is public and can be shared with future employers. Consider treating posts as part of your portfolio and edit the `/assets/style.css` to show off your design skills.

## What Happens Behind the Scenes
This template automatically:
- Builds your blog
- Converts Markdown into webpages
- Publishes your site online
You do not need to configure anything for this to work.

## Do Not Edit These Folders
These are automatically generated or required for publishing:
```
dist/
.github/
scripts/
```

## Optional: Preview Your Blog Locally
This is only needed if you want to test changes before publishing.
1. Install the required dependencies: `npm install`
1. Run the build script: `npm run build`

The generated files will be in the `dist` folder. You can launch this using Live Server in VSCode.
