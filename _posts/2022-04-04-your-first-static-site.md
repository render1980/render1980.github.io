---
layout: default
title: "Your first static site"
tag: study
---

## {{ page.title }}

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

Let's setup simple theme for our site.

Choose _Choose a theme_

![github choose theme](../../../images/your_first_static_site/gh_choose_theme.png)

You will see possible themes to choose then.

Let's choose **minimal** theme there.

![github themes](../../../images/your_first_static_site/gh_minimal_theme.png)

Next you will see the window with a suggestion to commit `README.md` file.

Click **Commit changes**

The first step is successfully completed! You can already see the result by the link: `https://{your_github_account_name}.github.io`

### Let's improve our site

#### Create simple layout

_Layout_ - is like a template with common structure that can be used for site pages.

Create new file **/\_layouts/default.html**.

![github create file](../../../images/your_first_static_site/gh_create_file.png)

![github create layout file](../../../images/your_first_static_site/gh_create_layout_file.png)

`jubilant-pancake` - just a name of my repository used for the demo.

Paste content into `default.html` below. Use can use [example](https://gist.githubusercontent.com/render1980/79fada63bd049f9fd0adbc87738f1db8/raw/4abb3844fe81661fe85252013c2a716ae397186d/default.html)

Click **Commit new file**

![github commit new file](../../../images/your_first_static_site/gh_commit_new_file.png)

#### Use created layout for the main page

Now we are ready to reuse the previously created template for our site pages.

Create **index.html** in the root, fill the content and commit changes.

You can use [example](https://gist.githubusercontent.com/render1980/79fada63bd049f9fd0adbc87738f1db8/raw/4c6a176d64ca6b362c57a180bc1594ac53eed0b8/index.html)
