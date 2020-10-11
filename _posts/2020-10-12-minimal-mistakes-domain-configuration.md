---
title: "minimal-mistakes: Domain configuration"
date: 2020-10-11T01:00:00
categories:
  - blog
tags:
  - Jekyll
  - minimal-mistakes
---

As stated in [Site base URL](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#site-base-url) when hosting your website on Github Pages you should specify `baseURL` to correspond to the URL format of Github project sites, i.e. "<username>.github.io/<project>". But when you assign a custom domain to the project and meanwhile force production environment by running:

```bash
bundle exec "JEKYLL_ENV`production jekyll serve -P 4001"
```

things get confusing. First of all, you're forcing production on local because some features require so when you're testing on local, such as `repository`, `comments`, `analytics`, etc. When you specify both `baseurl` and `repository`, e.g.

```yaml
baseurl: /blog
repository: ivanhjc/blog
```

everything is fine on `http://localhost:4001/blog/`. Since you have a custom domain you'd try to remove the `baseurl` and re-run the command. Now you'd see the site is messed up because it can't find the assets under the incorrectly parsed paths `pages/blog/assets/...`. If you change `repository`'s value to something else the paths would change accordingly. So MM is using `repository` to resolve the paths as well. You can remove both `baseurl` and `repository` and run without forcing production to make it right, but in this case comments would be lost as well... This is on the local.

When the code is pushed and viewd on Github Pages, with both keys removed, everything is fine on the custom domain - no baseurl and comments are shown. How Github builds and runs the code is unknown, but I guess that's the proper way for now to set up for a project hosted on Github Pages with custom domain. The usages of `baseurl` and `repository` should be further examined. Currently I haven't seen the problem being addressed anywhere in the doc and other places.
