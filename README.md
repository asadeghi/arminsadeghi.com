# arminsadeghi.com

Armin Sadeghi's personal blog. The original theme is based on [eleventy-base-blog v8](https://github.com/11ty/eleventy-base-blog): MIT license, Copyright (c) 2017–2023 Zach Leatherman @zachleat. All blog content is Copyright (c) 2024 Armin Sadeghi.

## Install dependencies

```
npm install
```

## Build

Generate a production-ready build to the `_site` folder:

```
npx @11ty/eleventy
```

Or build and host on a local development server:

```
npx @11ty/eleventy --serve
```

## Debug mode

MacOS or Linux

```
DEBUG=Eleventy* npx @11ty/eleventy
```

cmd.exe

```
set DEBUG=Eleventy* & npx @11ty/eleventy
```

Powershell

```
$env:DEBUG="Eleventy*"; npx @11ty/eleventy
```
