# WikiSpecies

WikiSpecies

## Usage

``` r
wt_wikispecies(name, utf8 = TRUE, ...)

wt_wikispecies_parse(
  page,
  types = c("langlinks", "iwlinks", "externallinks", "common_names", "classification"),
  tidy = FALSE
)

wt_wikispecies_search(query, limit = 10, offset = 0, utf8 = TRUE, ...)
```

## Arguments

- name:

  (character) Wiki name - as a page title, must be length 1

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

`wt_wikispecies` returns a list, with slots:

- langlinks - language page links

- externallinks - external links

- common_names - a data.frame with `name` and `language` columns

- classification - a data.frame with `rank` and `name` columns

`wt_wikispecies_parse` returns a list

`wt_wikispecies_search` returns a list with slots for `continue` and
`query`, where `query` holds the results, with `query$search` slot with
the search results

## References

<https://www.mediawiki.org/wiki/API:Search> for help on search

## Examples

``` r
if (FALSE) { # \dontrun{
# high level
wt_wikispecies(name = "Malus domestica")
wt_wikispecies(name = "Pinus contorta")
wt_wikispecies(name = "Ursus americanus")
wt_wikispecies(name = "Balaenoptera musculus")

# low level
pg <- wt_wiki_page("https://species.wikimedia.org/wiki/Abelmoschus")
wt_wikispecies_parse(pg)

# search wikispecies
# FIXME: utf=FALSE for now until curl::curl_escape fix 
# https://github.com/jeroen/curl/issues/228
wt_wikispecies_search(query = "pine tree", utf8=FALSE)

## use search results to dig into pages
res <- wt_wikispecies_search(query = "pine tree", utf8=FALSE)
lapply(res$query$search$title[1:3], wt_wikispecies)
} # }
```
