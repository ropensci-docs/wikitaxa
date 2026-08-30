# Parse MediaWiki Page URL

Parse a MediaWiki page url into its component parts (wiki name, wiki
type, and page title). Supports both static page urls and their
equivalent API calls.

## Usage

``` r
wt_wiki_url_parse(url)
```

## Arguments

- url:

  (character) MediaWiki page url.

## Value

a list with elements:

- wiki - wiki language

- type - wikipedia type

- page - page name

## See also

Other MediaWiki functions:
[`wt_wiki_page()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_page.md),
[`wt_wiki_page_parse()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_page_parse.md),
[`wt_wiki_url_build()`](https://docs.ropensci.org/wikitaxa/reference/wt_wiki_url_build.md)

## Examples

``` r
wt_wiki_url_parse(url="https://en.wikipedia.org/wiki/Malus_domestica")
#> $wiki
#> [1] "en"
#> 
#> $type
#> [1] "wikipedia"
#> 
#> $page
#> [1] "Malus_domestica"
#> 
wt_wiki_url_parse("https://en.wikipedia.org/w/api.php?page=Malus_domestica")
#> $wiki
#> [1] "en"
#> 
#> $type
#> [1] "wikipedia"
#> 
#> $page
#> [1] "Malus_domestica"
#> 
```
