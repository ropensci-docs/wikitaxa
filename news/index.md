# Changelog

## wikitaxa 0.5.0

CRAN release: 2026-02-13

#### BUG FIXES

- Removed dependency `WikidataR`, which was archived by CRAN, and
  replaced with direct calls to `WikipediR`
- Fixed bug when supplying common names to `wt_wikispecies_parse`
  ([\#21](https://github.com/ropensci/wikitaxa/issues/21))
- Fixed bug in `wt_data` when parsing some taxa
  ([\#25](https://github.com/ropensci/wikitaxa/issues/25))

## wikitaxa 0.4.0

CRAN release: 2020-06-29

#### MINOR IMPROVEMENTS

- remove docs link to httr that’s not used in package
  ([\#19](https://github.com/ropensci/wikitaxa/issues/19))
- remove egs from readme, change vignette name

## wikitaxa 0.3.0

CRAN release: 2018-10-19

#### MINOR IMPROVEMENTS

- integration with vcr for test caching for all HTTP requests
  ([\#17](https://github.com/ropensci/wikitaxa/issues/17))
  ([\#18](https://github.com/ropensci/wikitaxa/issues/18))
- link to `taxize` book and `wikitaxa` vignette in readme
  ([\#16](https://github.com/ropensci/wikitaxa/issues/16))

#### BUG FIXES

- fix to
  [`wt_wikipedia()`](https://docs.ropensci.org/wikitaxa/reference/wt_wikipedia.md)
  to separate `<br>` tags appropriately
  ([\#15](https://github.com/ropensci/wikitaxa/issues/15))

## wikitaxa 0.2.0

CRAN release: 2017-12-21

#### BUG FIXES

- [`wt_wikicommons()`](https://docs.ropensci.org/wikitaxa/reference/wt_wikicommons.md)
  fails better now when a page does not exist, and is now consitent with
  the rest of package
  ([\#14](https://github.com/ropensci/wikitaxa/issues/14))
- [`wt_wikicommons()`](https://docs.ropensci.org/wikitaxa/reference/wt_wikicommons.md)
  fixed - classification objects were not working correctly as the data
  used is a hot mess - tried to improve parsing of that text
  ([\#13](https://github.com/ropensci/wikitaxa/issues/13))
- [`wt_data()`](https://docs.ropensci.org/wikitaxa/reference/wt_data.md)
  fix - was failing due to i think a change in the internal pkg
  `WikidataR` ([\#12](https://github.com/ropensci/wikitaxa/issues/12))

## wikitaxa 0.1.4

CRAN release: 2017-05-05

#### NEW FEATURES

- [`wt_wikipedia()`](https://docs.ropensci.org/wikitaxa/reference/wt_wikipedia.md)
  and
  [`wt_wikipedia_search()`](https://docs.ropensci.org/wikitaxa/reference/wt_wikipedia.md)
  gain parameter `wiki` to give the wiki language, which defaults to
  `en` ([\#9](https://github.com/ropensci/wikitaxa/issues/9))

#### MINOR IMPROVEMENTS

- move some examples to dontrun
  ([\#11](https://github.com/ropensci/wikitaxa/issues/11))

## wikitaxa 0.1.0

CRAN release: 2017-04-03

#### NEW FEATURES

- Released to CRAN
