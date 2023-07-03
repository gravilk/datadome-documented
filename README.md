# Datadome documented & solved
This repository contains files that will make solving Datadome protection much easier, if not solve it instantly.
This solver worked on **7/3/2023**. It is very likely that something in their security changed since then. It is also possible for this solver to be flagging although I haven't noticed any signs of that happening yet.

## How Datadome works
The way Datadome works is simple. You only make one request to the url `https://api-js.datadome.co/js/` with some information about your browser and you get a `datadome` cookie back.
The data being sent by the browser is not encrypted or encoded but it is still hard to make sense of some values and their names.

## Big datadome oopsie
A few weeks back I was already preparing to make this solver for Reddit. I downloaded the script I had to deobfuscate but left it alone after a bit because I was busy with another project. After recently coming back I noticed that the Javascript for Datadome, specifically on Reddit is [unobfuscated](https://www.redditstatic.com/js/tags-slim.js).
I've archived this unobfuscated version in this repository in case they take it down as well as attached an obfuscated version of the script from another source.

## Highlights of the checks
As I've figured out what all the checks do I'll do a quick sum-up of what I've found.
- Screen size
- Time of execution of the script
- Basic renderer information
- (Mostly public) checks for webdrivers and evaluation libraries like JSDom
- Timezone
- Plugin information (could lead to revealing real browser)
- `eva` length check for the eval function. obscure check but could lead to revealing real browser
- Supported audio types
- Supported video types
- Checking if elements specific to different browsers exist
- Checking usb support

## How to try this and continue development?
The solver that worked on 7/3/2023 is in the `main.py` file. If you've noticed that Datadome added some new checks in the JSON they're sending. You will likely have to deobfuscate the script or find a website that has the script unobfuscated (for whatever reason). Then just search for the variable name you want and you'll likely quickly find what you're looking for. The only things you need for this solver to work are the site URL and site key which you can find in the API request.