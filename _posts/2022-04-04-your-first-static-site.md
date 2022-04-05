---
layout: default
title: "Your first static site"
tag: study
---

## {{ page.title }}

#### Content

<ul>
<li><a href="#create-github-account">Preparing</a>
<ul>
<li><a href="#create-github-account">Create Github account</a></li>
<li><a href="#create-new-repository">Create new repository</a></li>
<li><a href="#setup-github-pages">Setup github pages</a></li>
<li><a href="#activate-github-pages">Activate github pages</a></li>
<li><a href="#choose-theme">Choose theme</a></li>
</ul>
</li>
<li><a href="#lets-improve-our-site">Improving</a>
<ul>
<li><a href="#create-simple-layout">Create simple layout</a></li>
<li><a href="#use-created-layout-for-the-main-page">Use created layout for the main page</a></li>
<li><a href="#add-posts">Add posts</a></li>
<li><a href="#fix-the-links-and-names">Fix the links and names</a></li>
<li><a href="#what-is-next">What is next</a></li>
</ul>
</li>
</ul>

#### Create Github account

Open [github](https://github.com) in your browser and create new account.

![github signup](../../../images/your_first_static_site/gh_signup.png)

#### Create new repository

Go to _Repositories_ tab: `https://github.com/{your_github_account_name}?tab=repositories`.

Create new repository. Call it like `{your_github_account_name}.github.io`.

![new repository](../../../images/your_first_static_site/gh_new_repo.png)

#### Setup github pages

Go to _Settings_ tab: `https://github.com/{your_github_account_name}/{your_github_account_name}.github.io/settings`.

Click **Check it out here** in _GitHub Pages_ section.

![github github pages](../../../images/your_first_static_site/gh_gh_pages.png)

#### Activate Github Pages

Go to _Settings -> Pages_ section: `https://github.com/{your_github_account_name}/{your_github_account_name}.github.io/settings/pages`.

Choose: **Branch 'Main'**

Keep **/ (root)**

Click **Save**

![github pages activate](../../../images/your_first_static_site/gh_pages_activate.png)

After this step you will see 'Your site is ready to be published'.

#### Choose theme

Let's setup simple theme for our website.

Choose _Choose a theme_

![github choose theme](../../../images/your_first_static_site/gh_choose_theme.png)

You will see possible themes to choose then.

Let's choose **minimal** theme there.

![github themes](../../../images/your_first_static_site/gh_minimal_theme.png)

Next you will see the window with a suggestion to commit `README.md` file.

Click **Commit changes**

The first step is successfully completed! You can already see the result by the link: `https://{your_github_account_name}.github.io`

### Let's improve our website

#### Create simple layout

_Layout_ - is like a template with common structure that can be used for website pages.

Create new file **/\_layouts/default.html**.

![github create file](../../../images/your_first_static_site/gh_create_file.png)

![github create layout file](../../../images/your_first_static_site/gh_create_layout_file.png)

`jubilant-pancake` - just a name of my repository used for the demo.

Paste content into `default.html` below. Use this [example](https://gist.githubusercontent.com/render1980/79fada63bd049f9fd0adbc87738f1db8/raw/2c4dec44597580727318d2f8c642df4e9d200d10/default.html)

Click **Commit new file**

![github commit new file](../../../images/your_first_static_site/gh_commit_new_file.png)

#### Use created layout for the main page

Now we are ready to reuse the previously created template for our site pages.

Create **index.html** in the root, fill the content and commit changes.

You can use [example](https://gist.githubusercontent.com/render1980/79fada63bd049f9fd0adbc87738f1db8/raw/2c4dec44597580727318d2f8c642df4e9d200d10/index.html)

You can see the changes on your website less than in one minute. Go to the main page and refresh it. Wait until the changes become visible.

#### Add posts

You can use your static website like a blog. Let's create a simple example and see how we can use this function.

Open **index.html** and add [this code](https://gist.github.com/render1980/79fada63bd049f9fd0adbc87738f1db8#file-index_with_posts-html-L18-L20) to the bottom of the page.

It will make it possible to show a list with posts names on the main page.

If you go to your website you won't see any changes. Nothing has happened because you still haven't created any post. Let's change it.

Create new file **\_posts/2022-04-06-my-first-post.md**.

Paste

```
---
layout: default
title: "Jekyll: static websites generator"
tag: jekyll
---
```

inside of it and write e.g. `It's my first post and I did it myself!` below. Commit it.

Wait and check the changes on your website. The post name should apppear on the main page.

#### Fix the links and names

You can see that some names have `CHANGE_ME` prefix.

![change me](../../../images/your_first_static_site/change_me.png)

And now a small quest. Fix all names and links that are started from the prefix `CHANGE_ME`. All you need is in `default.html` layout.

When everything is fixed all links should work and all names should be correct.

#### What is next

If you want to make your website even better you can think about:

- Adding <a href="https://peterroelants.github.io/posts/adding-tags-to-github-pages/">tags that can organize your posts into categories</a>
- Making it possible to create <a href="https://stackoverflow.com/a/61740829">comments in your posts</a>
- Using other <a href="https://pages.github.com/themes/">themes</a>
- Creating your own style and replacing the stylesheets used in a theme
- Creating other pages
- Studying javascript and creating your own scripts to interact with a user
