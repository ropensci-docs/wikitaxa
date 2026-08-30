# Get MediaWiki Page from API

Supports both static page urls and their equivalent API calls.

## Usage

``` r
wt_wiki_page(url, ...)
```

## Arguments

- url:

  (character) MediaWiki page url.

- ...:

  Arguments passed to
  [`wt_wiki_url_build()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_url_build.md)
  if `url` is a static page url.

## Value

an `HttpResponse` response object from crul

## Details

If the URL given is for a human readable html page, we convert it to
equivalent API call - if URL is already an API call, we just use that.

## See also

Other MediaWiki functions:
[`wt_wiki_page_parse()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_page_parse.md),
[`wt_wiki_url_build()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_url_build.md),
[`wt_wiki_url_parse()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_url_parse.md)

## Examples

``` r
if (FALSE) { # \dontrun{
wt_wiki_page("https://en.wikipedia.org/wiki/Malus_domestica")
} # }
```
