---
title: "How to set up custom domain for Github Pages using minimal-mistakes"
last_modified_at: 2020-10-14
categories:
  - web
tags:
  - Jekyll
  - minimal-mistakes
  - blog
---

First you need to purchase a domain name from a seller. A domain name without the prefix like `ivanhjc.net` is called the root or apex domain, and a domain like `www.ivanhjc.net` or `blog.ivanhjc.net` is called a sub-domain. To use the root domain as the custom domain for Github Pages, you need to create an **A record** from your domain provider's admin panel like this:

| Name | Type | TTL | Data            |
| ---- | ---- | --- | --------------- |
| @    | A    | 1h  | 185.199.108.153 |
|      |      |     | 185.199.109.153 |
|      |      |     | 185.199.110.153 |
|      |      |     | 185.199.111.153 |

To use a subdomain create a **CNAME record** like this:

| Name  | Type  | TTL | Data              |
| ----- | ----- | --- | ----------------- |
| notes | CNAME | 1h  | ivanhjc.github.io |

Once the custom domain is properly configured, go to the project settings on Github, and then input the domain in the Custom Domain area.

For more details see:

- [Github help: About custom domains and GitHub Pages](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/about-custom-domains-and-github-pages)
- [Google help: Domain forwarding](https://support.google.com/domains/answer/4522141)
- [Google help: About resource records](https://support.google.com/domains/answer/3251147)

In the case of using minimal-mistakes you need to mind these properties: `url`, `baseurl`, and `repository`. As stated in [Site base URL](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#site-base-url) when hosting your website on Github Pages you need to specify `baseurl: <project>` to correspond to the URL format Github project sites use, i.e. `https://<username>.github.io/<project>/`, and when testing on local it runs on `http://localhost:4000/<project>/`. Since you have a custom domain you can omit `baseurl`. But if you're testing some features that require production environment such as `repository`, `comments`, `analytics`, etc. by running the following command:

``` bash
bundle exec "JEKYLL_ENV=production jekyll serve"
```
omitting `baseurl` would cause the path of assets to be wrongly parsed and the site would be a mess though it can be served. This is a bit confusing since the doc doesn't address this problem but with serveraltrials you could find that the path of assets is resolved with the `repository` value to something like this:

```
pages/<repository>/assets/...
```

Because without `repository` you can't run in production mode it seems to be a dead end for this sort of configuration, i.e., you can't run without `baseurl` as well. However, you can remove `baseurl` and`repository` and run in development mode on local, and when pushed to Github everything will work fine, including features that require production environment, such as comments.
