# Parse MediaWiki Page

Parses common properties from the result of a MediaWiki API page call.

## Usage

``` r
wt_wiki_page_parse(
  page,
  types = c("langlinks", "iwlinks", "externallinks"),
  tidy = FALSE
)
```

## Arguments

- page:

  ([crul::HttpResponse](https://docs.ropensci.org/crul/reference/HttpResponse.html))
  Result of
  [`wt_wiki_page()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_page.md)

- types:

  (character) List of properties to parse.

- tidy:

  (logical). tidy output to data.frames when possible. Default: `FALSE`

## Value

a list

## Details

Available properties currently not parsed: title, displaytitle, pageid,
revid, redirects, text, categories, links, templates, images, sections,
properties, ...

## See also

Other MediaWiki functions:
[`wt_wiki_page()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_page.md),
[`wt_wiki_url_build()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_url_build.md),
[`wt_wiki_url_parse()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_url_parse.md)

## Examples

``` r
if (FALSE) { # \dontrun{
pg <- wt_wiki_page("https://en.wikipedia.org/wiki/Malus_domestica")
wt_wiki_page_parse(pg)
} # }
```
