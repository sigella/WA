## 18.6 How vignettes are built and checked

We close this chapter by returning to a few workflow issues we didn’t cover in [Section 18.2](https://r-pkgs.org/vignettes.html#sec-vignettes-workflow-writing): How do the `.Rmd` files get turned into the vignettes consumed by users of an installed package? What does `R CMD check` do with vignettes? What are the implications for maintaining your vignettes?

It can be helpful to appreciate the big difference between the workflow for function documentation and vignettes. The source of function documentation is stored in roxygen comments in `.R` files below `R/.` We use [devtools::document()](https://devtools.r-lib.org/reference/document.html) to generate `.Rd` files below `man/`. These `man/*.Rd` files are part of the source package. The official R machinery cares only about the `.Rd` files.

Vignettes are very different because the `.Rmd` source is considered part of the source package and the official machinery (`R CMD build and check`) interacts with vignette source and built vignettes in many ways. The result is that the vignette workflow feels more constrained, since the official tooling basically treats vignettes somewhat like tests, instead of documentation.
