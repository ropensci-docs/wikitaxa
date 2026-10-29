# Build MediaWiki Page URL

Builds a MediaWiki page url from its component parts (wiki name, wiki
type, and page title). Supports both static page urls and their
equivalent API calls.

## Usage

``` r
wt_wiki_url_build(
  wiki,
  type = NULL,
  page = NULL,
  api = FALSE,
  action = "parse",
  redirects = TRUE,
  format = "json",
  utf8 = TRUE,
  prop = c("text", "langlinks", "categories", "links", "templates", "images",
    "externallinks", "sections", "revid", "displaytitle", "iwlinks", "properties")
)
```

## Arguments

- wiki:

  (character \| list) Either the wiki name or a list with `$wiki`,
  `$type`, and `$page` (the output of
  [`wt_wiki_url_parse()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_url_parse.md)).

- type:

  (character) Wiki type.

- page:

  (character) Wiki page title.

- api:

  (boolean) Whether to return an API call or a static page url
  (default). If `FALSE`, all following (API-only) arguments are ignored.

- action:

  (character) See <https://en.wikipedia.org/w/api.php> for supported
  actions. This function currently only supports "parse".

- redirects:

  (boolean) If the requested page is set to a redirect, resolve it.

- format:

  (character) See <https://en.wikipedia.org/w/api.php> for supported
  output formats.

- utf8:

  (boolean) If `TRUE`, encodes most (but not all) non-ASCII characters
  as UTF-8 instead of replacing them with hexadecimal escape sequences.

- prop:

  (character) Properties to retrieve, either as a character vector or
  pipe-delimited string. See
  <https://en.wikipedia.org/w/api.php?action=help&modules=parse> for
  supported properties.

## Value

a URL (character)

## See also

Other MediaWiki functions:
[`wt_wiki_page()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_page.md),
[`wt_wiki_page_parse()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_page_parse.md),
[`wt_wiki_url_parse()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_url_parse.md)

## Examples

``` r
wt_wiki_url_build(wiki = "en", type = "wikipedia", page = "Malus domestica")
#> [1] "https://en.wikipedia.org/wiki/Malus_domestica"
wt_wiki_url_build(
  wt_wiki_url_parse("https://en.wikipedia.org/wiki/Malus_domestica"))
#> [1] "https://en.wikipedia.org/wiki/Malus_domestica"
wt_wiki_url_build("en", "wikipedia", "Malus domestica", api = TRUE)
#> [1] "https://en.wikipedia.org/w/api.php?page=Malus_domestica&action=parse&redirects=TRUE&format=json&utf8=TRUE&prop=text%7Clanglinks%7Ccategories%7Clinks%7Ctemplates%7Cimages%7Cexternallinks%7Csections%7Crevid%7Cdisplaytitle%7Ciwlinks%7Cproperties"
```
