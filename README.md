# ArchR_Website

To build the website:

1. Make sure you have the most up-to-date version of the `DESCRIPTION` file and the `.Rd` files created from ArchR when the package is built. The `DESCRIPTION` file should be copied into the main folder of this repository. The `.Rd` files contain the function documentation and should be copied into `/man/`.
2. In the `DESCRIPTION` file, add the following tag "URL: https://www.ArchRProject.com"
3. You must have pandoc installed.
4. You must have the `pkgdown` R library installed.
5. In R, from the main repository directory (containing the index.md file), run `build_site()`. This will create a lot of HTML files in the `/docs/` folder.


To build the book:
1. Make sure the following packages are installed:
```
pdftools
```
2. Clone this `ArchR_Website` repository and navigate to the `/bookdown/` folder.
2. Delete the HTML files in the `/docs/bookdown` folder
3. Launch `R`
4. Load the `renv` environment and the `bookdown` package:
	```
	library(renv)
	renv::restore(lockfile="/path/to/lockfile")
	#follow instructions to activate and load libraries
	library(ArchR)
	library(bookdown)
	```
5. Run `bookdown::render_book(input = "index.Rmd", output_dir = "../docs/bookdown")`

Once you've built the book, copy all of the HTML files and required figures etc. into the `/docs/bookdown/` folder

#### Notes on bookdown installation and building

1. Because the v1.0.1 ArchR renv lockfile (as of 1/11/22) uses `xfun v0.28`, I had to manually install the `tinytex v0.35` prior to installing `bookdown` using
```
devtools::install_version("tinytex", version = "0.35", repos = "http://cran.us.r-project.org")
```

2. It seems like the building of the book struggles when packages need to be installed on the fly. This for example caused problems in the drosophila genome building section where bookdown just stalls

3. I am having trouble with conflicts between the renv packages and my locally installed packages?

4. library(parallel) causing problems in ArchR v1.0.1