# arminsadeghi.com

Personal blog built with the [Eleventy](https://www.11ty.dev/) site generator.

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
