# Wikipedia

Wikipedia

## Usage

``` r
wt_wikipedia(name, wiki = "en", utf8 = TRUE, ...)

wt_wikipedia_parse(
  page,
  types = c("langlinks", "iwlinks", "externallinks", "common_names", "classification"),
  tidy = FALSE
)

wt_wikipedia_search(
  query,
  wiki = "en",
  limit = 10,
  offset = 0,
  utf8 = TRUE,
  ...
)
```

## Arguments

- name:

  (character) Wiki name - as a page title, must be length 1

- wiki:

  (character) wiki language. default: en. See
  [wikipedias](https://docs.ropensci.org/wikitaxa/reference/wikipedias.md)
  for language codes.

- utf8:

  (logical) If `TRUE`, encodes most (but not all) non-ASCII characters
  as UTF-8 instead of replacing them with hexadecimal escape sequences.
  Default: `TRUE`

- ...:

  curl options, passed on to
  [`httr::GET()`](https://httr.r-lib.org/reference/GET.html)

- page:

  ([`httr::response()`](https://httr.r-lib.org/reference/response.html))
  Result of
  [`wt_wiki_page()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_page.md)

- types:

  (character) List of properties to parse

- tidy:

  (logical). tidy output to data.frame's if possible. Default: `FALSE`

- query:

  (character) query terms

- limit:

  (integer) number of results to return. Default: 10

- offset:

  (integer) record to start at. Default: 0

## Value

`wt_wikipedia` returns a list, with slots:

- langlinks - language page links

- externallinks - external links

- common_names - a data.frame with `name` and `language` columns

- classification - a data.frame with `rank` and `name` columns

- synonyms - a character vector with taxonomic names

`wt_wikipedia_parse` returns a list with same slots determined by the
`types` parmeter

`wt_wikipedia_search` returns a list with slots for `continue` and
`query`, where `query` holds the results, with `query$search` slot with
the search results

## References

<https://www.mediawiki.org/wiki/API:Search> for help on search

## Examples

``` r
if (FALSE) { # \dontrun{
# high level
wt_wikipedia(name = "Malus domestica")
wt_wikipedia(name = "Malus domestica", wiki = "fr")
wt_wikipedia(name = "Malus domestica", wiki = "da")

# low level
pg <- wt_wiki_page("https://en.wikipedia.org/wiki/Malus_domestica")
wt_wikipedia_parse(pg)
wt_wikipedia_parse(pg, tidy = TRUE)

# search wikipedia
# FIXME: utf=FALSE for now until curl::curl_escape fix 
# https://github.com/jeroen/curl/issues/228
wt_wikipedia_search(query = "Pinus", utf8=FALSE)
wt_wikipedia_search(query = "Pinus", wiki = "fr", utf8=FALSE)
wt_wikipedia_search(query = "Pinus", wiki = "br", utf8=FALSE)

## curl options
# wt_wikipedia_search(query = "Pinus", verbose = TRUE, utf8=FALSE)

## use search results to dig into pages
res <- wt_wikipedia_search(query = "Pinus", utf8=FALSE)
lapply(res$query$search$title[1:3], wt_wikipedia)
} # }
```
