# Wikidata taxonomy data

Wikidata taxonomy data

## Usage

``` r
wt_data(x, property = NULL, ...)

wt_data_id(x, language = "en", limit = 10, ...)
```

## Arguments

- x:

  (character) a taxonomic name

- property:

  (character) a property id, e.g., P486

- ...:

  curl options passed on to
  [`httr::GET()`](https://httr.r-lib.org/reference/GET.html)

- language:

  (character) two letter language code

- limit:

  (integer) records to return. Default: 10

## Value

`wt_data` searches Wikidata, and returns a list with elements:

- labels - data.frame with columns: language, value

- descriptions - data.frame with columns: language, value

- aliases - data.frame with columns: language, value

- sitelinks - data.frame with columns: site, title

- claims - data.frame with columns: claims, property_value,
  property_description, value (comma separated values in string)

`wt_data_id` gets the Wikidata ID for the searched term, and returns the
ID as character

## Details

Note that `wt_data` can take a while to run since when fetching claims
it has to do so one at a time for each claim

You can search things other than taxonomic names with `wt_data` if you
like

## Examples

``` r
if (FALSE) { # \dontrun{
# search by taxon name
wt_data("Mimulus alsinoides")

# choose which properties to return
wt_data(x="Mimulus foliatus", property = c("P846", "P815"))

# get a taxonomic identifier
wt_data_id("Mimulus foliatus")

# the id can be passed directly to wt_data()
wt_data(wt_data_id("Mimulus foliatus"))
} # }
```
