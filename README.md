# sandpiper-web
Landing page for sandpiper project

## Static Site Generator
We use [Hugo](https://gohugo.io/) to build the Sandpiper website with the beautiful [Docsy](https://www.docsy.dev/) theme for content styling.

## Hosting
We are currently hosting this website on [Render](https://render.com/) with automatic https certificate updates and automatic updates from GitHub pushes. The render url is https://sandpiper.onrender.com/, but our own custom domain is https://sandpiperframework.org.

### Hosted Build Command (Render, Netlify, etc.)

Since the Docsy theme is included as a Git `submodule`, you must update from that repo to get all required files.

```
cd themes/docsy && git submodule update -f --init && cd ../.. && hugo --gc --minify
```

## Local Development

1. This project requires Hugo **"extended version"** (0.53 or later) which supports SCCS. Look for `hugo_extended_` at bottom of the Assets list:

```
https://github.com/gohugoio/hugo/releases
```

There are no dependencies, simply save the executable to a directory in your PATH and you should be good to go!

2. If you want to add or override any css settings, you must install Nodejs and [PostCSS](https://postcss.org/). Hugo will take it from there. See the instructions here:

```
https://www.docsy.dev/docs/getting-started/#install-postcss
```

3. Make a local working copy using git (leaving off a target directory will create `sandpiper-web` automatically):

```
git clone https://github.com/dougwinsby/sandpiper-web.git
```

4. Change directory to the root of the cloned project:

```
cd sandpiper-web
```

5. Get local copies of the Docsy theme submodules so you can build and run your site locally:

```
git submodule update --init --recursive
```

6. Build your site:

```
hugo server
```

7. Preview your site in your browser at: http://localhost:1313/. Ctrl-C will stop the Hugo server.

## Authoring New Content

All text content (beyond what is embedded in the theme design and over-ridden by The Sandpiper Authors when customizing the site) is maintained in markdown (.md) files within language-specific Content directories (e.g. `content/en/`). Files in these content root directories are typically grouped in subdirectories corresponding to your site’s sections and templates. You can find more information here:

```
https://www.docsy.dev/docs/adding-content/content/#content-sections-and-templates
```

You can use regular Markdown to add inline images. Thise images should be saved to the site’s `static` directory. If you need more control over scaling and sizing, you can use the Docsy [imgproc](https://www.docsy.dev/docs/adding-content/shortcodes/#imgproc) "shortcode" as shown here:

```
{{< imgproc spruce Fill "400x450" >}}
Norway Spruce Picea abies shoot with foliage buds.
{{< /imgproc >}}
```

When using the `imgproc` shortcode, store the image in the associated [Page Bundle](https://gohugo.io/content-management/page-bundles/) which is usually the same directory as the `_index.md` file.

## Copyright

Please see the LICENSE file for details.
