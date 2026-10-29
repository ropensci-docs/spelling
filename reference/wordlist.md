# The WORDLIST file

The package wordlist file is used to allow custom words which will be
added to the dictionary when spell checking. It is stored in
`inst/WORDLIST` in the source package and must contain one word per line
in UTF-8 encoded text.

## Usage

``` r
update_wordlist(pkg = ".", vignettes = TRUE, confirm = TRUE)

get_wordlist(pkg = ".")
```

## Arguments

- pkg:

  path to package root directory containing the `DESCRIPTION` file

- vignettes:

  check all `rmd` and `rnw` files in the pkg root directory (e.g.
  `readme.md`) and package `vignettes` folder.

- confirm:

  show changes and ask confirmation before adding new words to the list

## Details

The update_wordlist function runs a full spell check on a package, shows
the results, and then prompts to add the found words to the package
wordlist. Obviously you should check closely that these legitimate words
and not actual spelling errors. It also removes words from the wordlist
that no longer appear as spelling errors, either because they have been
removed from the documentation or added to the `lang` dictionary.

## See also

Other spelling:
[`spell_check_files()`](https://docs.ropensci.org/spelling/reference/spell_check_files.md),
[`spell_check_package()`](https://docs.ropensci.org/spelling/reference/spell_check_package.md)
