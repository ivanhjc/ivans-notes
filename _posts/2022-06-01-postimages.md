---
title: "Weird behavior of direct links from postimages.org"
excerpt: ""
last_modified_at: 2022-06-01
categories:
  - Web
tags:
  - Image
---

In this [demo](/_demo/postimages.org_image_test.html):

``` html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>Image size test</title>
  </head>
  <body>
	<img src="https://i.postimg.cc/kXzT5mbK/screenshot-2021-09-09-eshell-coding-mismatch.png" alt="1"><br>
	<img src="https://i.postimg.cc/kXzT5-mbK/screenshot-2021-09-09-eshell-coding-mismatch.png" alt="2"><br>
	<img src="https://i.postimg.cc/Hx4Swwdp/Piano-Roll-How-to-Chord-sounding-Indefinitely-Solved.jpg" alt="3"><br>
	<img src="https://i.postimg.cc/Hx4Sw-wdp/Piano-Roll-How-to-Chord-sounding-Indefinitely-Solved.jpg" alt="4">
  </body>
</html>
```

there are four direct links, which are all supposed to load the original-sized images when used in `<img>` tags. However, in reality they have been shown differently in Chrome and Firefox. Their behaviors are summed up to the following table, where each image numbered 1 to 4 (marked in their `alt` value) is opened directly in the browser and from the `<img>` tag, and "original" means the link is opend as the original-sized image, "redirect" means it redirects to another webpage, and "thumbnail" means it is opend as a resolution-reduced thumbnail.

| Image    | 1         | 2        | 3        | 4        |
|----------|-----------|----------|----------|----------|
| Firefox  |           |          |          |          |
| Directly | original  | redirect | redirect | original |
| \<img>   | thumbnail | original | original | original |
| Chrome   |           |          |          |          |
| Directly | original  | redirect | redirect | redirect |
| \<img>   | original  | original | original | original |

Link 1 is the direct link copied from <https://postimg.cc/YhN6XT8C>

<figure>
	<a href="https://i.postimg.cc/z5LPFBms/Snipaste-2022-06-01-13-03-30.png"><img src="https://i.postimg.cc/z5LPFBms/Snipaste-2022-06-01-13-03-30.png"></a>
</figure>

and is the one that I thought should display the original-sized image but actually displayed a blurry thumbnail. But this only occurred on Firefox. In Chrome it was displayed as the original-sized image. From the inspector of Firefox I could see the actual image retrieved was a much smaller one. Then I found link 3 and 4 that could be displayed in their original size. You can see a slight difference between them, that is, link 4 has an extra hypen. So I tried to mimic this to get link 2 and it worked!

This problem was spotted when I wrote this [post]({{site.baseurl}}/emacs/emacs-encoding) where the screenshots were displayed as blurry thumbnails. At first I thought it's a problem of [minimal-mistakes](https://mmistakes.github.io/minimal-mistakes/) but then narrowed it down to the links themselves. The solution is adding an extra hypen before the antepenultimate character!

**Update**: After I fiddled around with the demo suddenly the original link (link 1) somehow displayed the original-sized image in Firefox! Now I have no idea what's going on. Maybe it's because of the network because I turned on my proxy for a while. Maybe it's because the server of <https://postimages.org> detected that someone was trying desperately to get this link right...


**Update**: After I cleared the cookies and cache all links above if opend from `<img>` couldn't be displayed as original-sized images but returned to blurry thumbnails no matter the browser in use. I guess the reason why they could display as original-sized images at some point is because the browsers were loading them from the cache and those original-sized images were cached at some point! I still don't know why they weren't always displayed and how to force them to display in their original size. Guess I just have to change to another image hosting service provider.

**Update**: Finally I can say for sure what's causing all the fuss. It's because of the network! As all the troubles the GFW has caused this is just yet another one. When I cleared the cache and turned on my proxy every link could display in their original size no matter the browser. It appears postimages.org could still send a thumbnail even if the link was blocked. I feel the effort in making information more transcendent!
