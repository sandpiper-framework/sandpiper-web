# sandpiper-web
Landing page for sandpiper project

## Static Site Generator
We use [Hugo](https://gohugo.io/) to build the Sandpiper website with the beautiful [Docsy](https://www.docsy.dev/) theme for content styling.

## Hosting
We are currently hosting this website on [Render](https://render.com/) with automatic https certificate updates and automatic updates from GitHub pushes. The render url is https://sandpiper.onrender.com/, but the public access is through our custom domain (xxxx.com).

### Build Command

Since the Docsy theme is included as Git `submodule`, you should update from that repo to get the latest theme version.

```
cd themes/docsy && git submodule update -f --init && cd ../.. && hugo --gc --minify
```

### Local Development

1. This project requires Hugo **"extended version"** (0.53 or later) which supports SCCS. Look for `hugo_extended_` at bottom of the Assets list:

```
https://github.com/gohugoio/hugo/releases
```

2. If you need to change (or override) css settings, you must Nodejs and PostCSS. See the instructions here:

```
https://www.docsy.dev/docs/getting-started/#install-postcss
```

3. Make a local working copy using git:

```
git clone https://github.com/dougwinsby/sandpiper-web.git
```

4. Change directory to the root of the cloned project, for example:

```
cd sandpiper-web
```

5. Get local copies of the project submodules so you can build and run your site locally:

```
git submodule update --init --recursive
```

6. Build your site:

```
hugo server
```

7. Preview your site in your browser at: http://localhost:1313/. You can use Ctrl-C to stop the Hugo server.
