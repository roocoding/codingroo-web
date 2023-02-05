---
title: "Adding a Page Counter to Hugo"
date: 2023-02-05T15:29:33+10:00
categories: ["Hugo"]
---

# Adding a Page Counter to Hugo

Hugo is a fast and flexible static site generator that you can use to build a variety of websites, including blogs. In this tutorial, we'll show you how to add a page counter to your Hugo site.

## Step 1: Install the Page Counter Package

To add a page counter to your Hugo site, you'll need to install a package that provides the functionality. One of the most popular options is the `hugo-page-counter` package. To install it, run the following command in your terminal:

```
$ go get -u github.com/shenoybr/hugo-page-counter
```

## Step 2: Add the Counter Code to Your Site

Once you've installed the page counter package, you need to add the code that will display the counter on your site. Add the following code to your Hugo template:

···
{{ $counter := .Site.GetPage "counter.md" }}
{{ $counter.Content | safeHTML }}
···


This code uses the `.Site.GetPage` method to get the content of a page called `counter.md`, which will be used to display the counter on your site.

## Step 3: Create the Counter Page

Next, create the `counter.md` page that was referenced in the code above. To do this, create a new file in your Hugo content directory with the following contents:

```
---
title: "Page Counter"
---

<div class="counter">
  <script src="https://cdn.rawgit.com/shenoybr/hugo-page-counter/v1.0.0/counter.js"></script>
</div>

```

This file defines the title of the page and includes a script that provides the functionality of the page counter.

## Step 4: Deploy Your Site

Finally, you'll need to deploy your Hugo site so that the changes you made will be reflected on your live site. To do this, run the following command in your terminal:

```
hugo -D
```

This command will generate the static files for your site and output them to the `public` directory. You can then upload these files to your web server to make your site live.

## Conclusion

That's it! You've successfully added a page counter to your Hugo site. You can now see how many visitors your site has received and track its growth over time.