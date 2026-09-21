# Arora Price Tool

A free, static, client-side tool for looking up part numbers across multiple Excel price lists at once.

**Live:** https://arorapricetool.vercel.app

## What it does

Upload one or more Excel price lists (`.xlsx`, `.xlsm`, `.xls`), tell it once which columns hold the part number / price / description for each file, then search one or many part numbers at a time. It searches across every uploaded file simultaneously and shows which file/brand each match came from, with a one-click copy of `Part Number - Description - Price`.

## Why it's built this way

Everything runs entirely in the browser — file parsing ([SheetJS](https://github.com/SheetJS/sheetjs) via CDN), column auto-detection, search, and persistence (via IndexedDB, so uploaded files and their column setups survive a page reload) all happen client-side. There is no backend and no server ever sees the uploaded files, which means:

- It's a plain static site — free to host indefinitely on Vercel's Hobby tier
- No privacy concerns, since nobody's price list data ever leaves their own browser
- No auth needed, since there's no shared/server-side data to protect

## Stack

- Single self-contained `index.html` (vanilla JS + CSS, no build step, no framework)
- [SheetJS (xlsx)](https://cdn.jsdelivr.net/npm/xlsx@0.18.5/dist/xlsx.full.min.js) loaded from a CDN for Excel parsing
- Deployed on [Vercel](https://vercel.com)

## Running locally

No build step needed — just serve the folder:

```bash
python3 -m http.server 8899
```

Then open `http://127.0.0.1:8899`.

## Deploying

```bash
vercel --prod
```
