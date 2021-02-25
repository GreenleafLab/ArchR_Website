# ArchR_Website

To build the website:

1. Make sure you have the most up-to-date version of the `DESCRIPTION` file and the `.Rd` files created from ArchR when the package is build. The `DESCRIPTION` file should be copied into the main folder of this repository. The `.Rd` files contain the function documentation and should be copied into `/man/`.
2. In the `DESCRIPTION` file, add the following tag "URL: https://www.ArchRProject.com"
3. You must have pandoc installed.
4. You must have the `pkgdown` R library installed.
5. In R, from the main repository directory (containing the index.md file), run `build_site()`. This will create a lot of HTML files in the `/docs/` folder.


To build the book:

Once you've build the book, copy all of the HTML files and required figures etc. into the `/docs/bookdown/` folder