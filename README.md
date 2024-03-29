# YRSS

YRSS is a jQuery plugin that utilizes YQL (Yahoo Query Language) to retrieve RSS (Really Simple Syndication) feed data and display it on an HTML page. It's loosely based off of [zRSSFeed](http://www.zazar.net/developers/jquery/zrssfeed/), which has been discontinued due to the [Google Feed API being deprecated](https://developers.google.com/feed/terms). This is our solution for clients that previously had zRSSFeed customizations made in BBNC/BBIS that no longer work.

YRSS can be used to pull data from any RSS feed on the Internet. However, as with any 3rd party service there's always a chance it will go down or become unusable in the future. Let's hope that Yahoo! keeps YQL up and running.

## CORS

CORS stands for Cross-Origin Resource Sharing. It's a mechanism that allows restricted resources on a web page to be requested from another domain outside the domain from which the resource originated ([Wikipedia](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing)).

YRSS bypasses CORS restrictions (if any) by requesting a JSON response at the end of the YQL query (`&format=json`). This allows you to grab RSS feed data from any source on the Internet.

## Setup

Copy the contents of [yrss.js](yrss.js) and paste it at the bottom of your client's global namespace file under **PLUGINS**.

## Initialization

The following code snippet demonstrates how to initialize the plugin on an HTML element. It includes all options and their default values:

```js
$('#element').rssfeed('https://bbis5740pssandbox.blackbaudhosting.com/feed.rss?id=1', {
    ssl: false,
    limit: 10,
    showerror: true,
    errormsg: '',
    tags: false,
    date: true,
    dateformat: 'default',
    titletag: 'h4',
    content: true,
    snippet: true,
    snippetlimit: 120,
    linktarget: '_self'
}, function () {
    // optional callback function
});
```

### Callback Function

As above, you can pass a callback function after the options are decalred. This function will fire immediately after YQL returns feed data.

**Format:** `rssfeed(url, options, fn)`

## Configuration

`ssl`: (**boolean**) - enable or disable **https** protocol

`limit`: (**integer**) - number of entries to display

`showerror`: (**boolean**) - display error message if feed cannot be loaded

`errormsg`: (**string**) - display custom error message if `showerror` option is **true**

`tags`: (**boolean**) - enable or disable tagging (entry tags are added as data attribute values on entry wrapper elements)

`date`: (**boolean**) - enable or disable entry dates

`dateformat`: (**string**) - accepts **default**, **spellmonth**, **localedate**, and **localedatetime** if `date` option is **true**

`titletag`: (**string**) - accepts any HTML heading tag

`content`: (**boolean**) - show or hide entry content (entry title and entry date will still be displayed)

`snippet`: (**boolean**) - entry image is moved above entry title and only first paragraph in content is displayed

`snippetlimit`: (**integer**) - character limit of first paragraph in content if `snippet` option is **true**

`linktarget`: (**string**) - accepts **_self**, **_blank**, **_parent**, and **_top**

## How to Contribute

Team contributions are how we keep our code great. Please adhere to the following guidelines.

### Workflow

For code changes, you'll need to submit a pull request. If you've never submitted one, it's easy. Just follow the [contribution docs](https://guides.github.com/introduction/flow/).

Basically:

1. Create a branch
2. Add commits
3. Open a Pull Request
4. Deploy
5. Merge (and delete branch if no longer needed)

## Suggestions / Concerns?

Please use the issue tracker in this repo to report bugs or suggest improvements.
