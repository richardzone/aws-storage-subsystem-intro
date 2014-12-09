# The Guide for New Media Guide

We're using [GitBook](https://github.com/GitbookIO/gitbook) to generate our guide.


## Install it the hard way

Here's a step by step guide for how to use it.

- Node environment
- Install GitBook, you can refer to its github page, or just run  
  - `npm install` for this folder only
- Run `npm run build` in this repo's root folder to generate the gitbook
- Run `npm run server` in this repo's root folder to host the gitbook (default http://localhost:3000, your can set `PORT=5000` to change)
- Run `npm start` for quick start

- or Go to /public, you have several choices:
  - `open index.html` this is very straight forward
  - `python -m SimpleHTTPServer`, then go ``http://localhost:8000` for a friendly URL and search function.
  - `php -S localhost:8000`, then go `http://localhost:8000`. this is the same as above.

## Install it the stupid way

- `npm i`
- `npm start`
- DONE

## Other informations
> For some reasons:
  1. each time when we complete the edit, we need to rebuild it again
  2. the server has caches

- I add a **watch** feature to our project, after we start our server, we no need to rebuild the project agagin.
- Be sure run `npm i` before you `npm start`.
- Use the default server to `watch` and `livereload`.

## How to contribute

Please refer to [GitBook](https://github.com/GitbookIO/gitbook).
