# Package Spell Checking

Automatically spell-check package description, documentation, and
vignettes.

## Usage

``` r
spell_check_package(pkg = ".", vignettes = TRUE, use_wordlist = TRUE)

spell_check_setup(pkg = ".", vignettes = TRUE, lang = "en-US", error = FALSE)
```

## Arguments

- pkg:

  path to package root directory containing the `DESCRIPTION` file

- vignettes:

  check all `rmd` and `rnw` files in the pkg root directory (e.g.
  `readme.md`) and package `vignettes` folder.

- use_wordlist:

  ignore words in the package
  [WORDLIST](https://docs.ropensci.org/spelling/reference/wordlist.md)
  file

- lang:

  set `Language` field in `DESCRIPTION` e.g. `"en-US"` or `"en-GB"`. For
  supporting other languages, see the [hunspell
  vignette](https://docs.ropensci.org/hunspell/articles/intro.html#hunspell-dictionaries).

- error:

  should `CMD check` fail if spelling errors are found? Default only
  prints results.

## Details

Parses and checks R manual pages, rmd/rnw vignettes, and text fields in
the package `DESCRIPTION` file.

The preferred spelling language (typically `en-GB` or `en-US`) should be
specified in the `Language` field from your package `DESCRIPTION`. To
allow custom words, use the package
[WORDLIST](https://docs.ropensci.org/spelling/reference/wordlist.md)
file which will be added to the dictionary when spell checking. See
[update_wordlist](https://docs.ropensci.org/spelling/reference/wordlist.md)
to automatically populate and update this file.

The spell_check_setup function adds a unit test to your package which
automatically runs a spell check on documentation and vignettes during
`R CMD check` if the environment variable `NOT_CRAN` is set to `TRUE`.
By default this unit test never fails; it merely prints potential
spelling errors to the console. If not already done, the
spell_check_setup function will add `spelling` as a `Suggests`
dependency, and a `Language` field to `DESCRIPTION`.

Hunspell includes dictionaries for `en_US` and `en_GB` by default. Other
languages require installation of a custom dictionary, see
[hunspell](https://docs.ropensci.org/hunspell/reference/hunspell.html)
for details.

## See also

Other spelling:
[`spell_check_files()`](https://docs.ropensci.org/spelling/reference/spell_check_files.md),
[`wordlist`](https://docs.ropensci.org/spelling/reference/wordlist.md)
