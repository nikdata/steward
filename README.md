
<!-- README.md is generated from README.Rmd. Please edit that file -->

# steward

<!-- badges: start -->

<!-- badges: end -->

The goal of steward is to enable a package developer to embed a data
dictionary within their package using the Roxygen syntax. This results
in users being able to pull up the data dictionary using the helper
function and view the appropriate help document.

In the past, the developer would have to code by hand using Roxygen
syntax the data dictionary. This can lead to increased development time
and frustration. However, the Steward package aims to take a data
dictionary in either a YAML or CSV format and automatically create a
Roxygen output for the data dictionary contents.

## Class

The steward package is equipped with its own S3 class (called
`"stw_meta"`) that enables it to seamlessly read in either a YAML or CSV
file and convert to a Roxygen syntax.

## Installation

You can install the development version of steward from
[GitHub](https://github.com/uncoast-unconf/steward) with:

## Example: Read YAML

This is a basic example which shows you how to solve a common problem:

``` r
library(steward)
stw_read_yaml(system.file("metadata/diamonds.yaml", package = "steward"))
#> $name
#> [1] "diamonds"
#> 
#> $title
#> [1] "Prices of 50,000 round cut diamonds"
#> 
#> $description
#> [1] "A dataset containing the prices and other attributes of almost 54,000 diamonds."
#> 
#> $source
#> [1] "www.google.com"
#> 
#> $n_row
#> NULL
#> 
#> $n_col
#> NULL
#> 
#> $dictionary
#>       name      type
#> 1    price    double
#> 2    carat    double
#> 3      cut character
#> 4    color character
#> 5  clarity character
#> 6        x    double
#> 7        y    double
#> 8        z    double
#> 9    depth    double
#> 10   table    double
#>                                                                                          description
#> 1                                                               price in US dollars ($326 - $18,823)
#> 2                                                                     weight of diamond (0.2 - 5.01)
#> 3                                         quality of the cut (Fair, Good, Very Good, Premium, Ideal)
#> 4                                                          diamond color, from D (best) to J (worst)
#> 5  a measurement of how clear the diamond is (I1 (worst), SI2, SI1, VS2, VS1, VVS2, VVS1, IF (best))
#> 6                                                                             length in mm (0-10.74)
#> 7                                                                               width in mm (0-58.9)
#> 8                                                                               depth in mm (0-31.8)
#> 9                                  total depth percentage = z / mean(x, y) = 2 * z / (x + y) (43-79)
#> 10                                          width of top of diamond relative to widest point (43-95)
#> 
#> attr(,"class")
#> [1] "stw_meta"
```

## Example - Create Roxygen Meta

``` r

stw_to_roxygen(diamonds_meta)
#> #' Prices of 50,000 round cut diamonds
#> #' 
#> #' A dataset containing the prices and other attributes of almost 54,000 diamonds.
#> #' 
#> #' @format A data frame with 53940 rows and 10 variables:
#> #' 
#> #' \describe{ 
#> #'   \item{price}{price in US dollars ($326 - $18,823)}
#> #'   \item{carat}{weight of diamond (0.2 - 5.01)}
#> #'   \item{cut}{quality of the cut (Fair, Good, Very Good, Premium, Ideal)}
#> #'   \item{color}{diamond color, from D (best) to J (worst)}
#> #'   \item{clarity}{a measurement of how clear the diamond is (I1 (worst), SI2, SI1, VS2, VS1, VVS2, VVS1, IF (best))}
#> #'   \item{x}{length in mm (0-10.74)}
#> #'   \item{y}{width in mm (0-58.9)}
#> #'   \item{z}{depth in mm (0-31.8)}
#> #'   \item{depth}{total depth percentage = z / mean(x, y) = 2 * z / (x + y) (43-79)}
#> #'   \item{table}{width of top of diamond relative to widest point (43-95)}
#> #' }
#> #' @source www.google.com
#> "diamonds"
```

## Example - GT table

``` r
stw_to_table(diamonds_meta)
```

<!--html_preserve-->

<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#agautcviel .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #000000;
  font-size: 16px;
  background-color: #FFFFFF;
  /* table.background.color */
  width: auto;
  /* table.width */
  border-top-style: solid;
  /* table.border.top.style */
  border-top-width: 2px;
  /* table.border.top.width */
  border-top-color: #A8A8A8;
  /* table.border.top.color */
}

#agautcviel .gt_heading {
  background-color: #FFFFFF;
  /* heading.background.color */
  border-bottom-color: #FFFFFF;
}

#agautcviel .gt_title {
  color: #000000;
  font-size: 125%;
  /* heading.title.font.size */
  padding-top: 4px;
  /* heading.top.padding */
  padding-bottom: 1px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#agautcviel .gt_subtitle {
  color: #000000;
  font-size: 85%;
  /* heading.subtitle.font.size */
  padding-top: 1px;
  padding-bottom: 4px;
  /* heading.bottom.padding */
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#agautcviel .gt_bottom_border {
  border-bottom-style: solid;
  /* heading.border.bottom.style */
  border-bottom-width: 2px;
  /* heading.border.bottom.width */
  border-bottom-color: #A8A8A8;
  /* heading.border.bottom.color */
}

#agautcviel .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  padding-top: 4px;
  padding-bottom: 4px;
}

#agautcviel .gt_col_heading {
  color: #000000;
  background-color: #FFFFFF;
  /* column_labels.background.color */
  font-size: 16px;
  /* column_labels.font.size */
  font-weight: initial;
  /* column_labels.font.weight */
  vertical-align: middle;
  padding: 10px;
  margin: 10px;
}

#agautcviel .gt_sep_right {
  border-right: 5px solid #FFFFFF;
}

#agautcviel .gt_group_heading {
  padding: 8px;
  color: #000000;
  background-color: #FFFFFF;
  /* row_group.background.color */
  font-size: 16px;
  /* row_group.font.size */
  font-weight: initial;
  /* row_group.font.weight */
  border-top-style: solid;
  /* row_group.border.top.style */
  border-top-width: 2px;
  /* row_group.border.top.width */
  border-top-color: #A8A8A8;
  /* row_group.border.top.color */
  border-bottom-style: solid;
  /* row_group.border.bottom.style */
  border-bottom-width: 2px;
  /* row_group.border.bottom.width */
  border-bottom-color: #A8A8A8;
  /* row_group.border.bottom.color */
  vertical-align: middle;
}

#agautcviel .gt_empty_group_heading {
  padding: 0.5px;
  color: #000000;
  background-color: #FFFFFF;
  /* row_group.background.color */
  font-size: 16px;
  /* row_group.font.size */
  font-weight: initial;
  /* row_group.font.weight */
  border-top-style: solid;
  /* row_group.border.top.style */
  border-top-width: 2px;
  /* row_group.border.top.width */
  border-top-color: #A8A8A8;
  /* row_group.border.top.color */
  border-bottom-style: solid;
  /* row_group.border.bottom.style */
  border-bottom-width: 2px;
  /* row_group.border.bottom.width */
  border-bottom-color: #A8A8A8;
  /* row_group.border.bottom.color */
  vertical-align: middle;
}

#agautcviel .gt_striped {
  background-color: #f2f2f2;
}

#agautcviel .gt_from_md > :first-child {
  margin-top: 0;
}

#agautcviel .gt_from_md > :last-child {
  margin-bottom: 0;
}

#agautcviel .gt_row {
  padding: 10px;
  /* row.padding */
  margin: 10px;
  vertical-align: middle;
}

#agautcviel .gt_stub {
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #A8A8A8;
  padding-left: 12px;
}

#agautcviel .gt_stub.gt_row {
  background-color: #FFFFFF;
}

#agautcviel .gt_summary_row {
  background-color: #FFFFFF;
  /* summary_row.background.color */
  padding: 6px;
  /* summary_row.padding */
  text-transform: inherit;
  /* summary_row.text_transform */
}

#agautcviel .gt_first_summary_row {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
}

#agautcviel .gt_table_body {
  border-top-style: solid;
  /* table_body.border.top.style */
  border-top-width: 2px;
  /* table_body.border.top.width */
  border-top-color: #A8A8A8;
  /* table_body.border.top.color */
  border-bottom-style: solid;
  /* table_body.border.bottom.style */
  border-bottom-width: 2px;
  /* table_body.border.bottom.width */
  border-bottom-color: #A8A8A8;
  /* table_body.border.bottom.color */
}

#agautcviel .gt_footnote {
  font-size: 90%;
  /* footnote.font.size */
  padding: 4px;
  /* footnote.padding */
}

#agautcviel .gt_sourcenote {
  font-size: 90%;
  /* sourcenote.font.size */
  padding: 4px;
  /* sourcenote.padding */
}

#agautcviel .gt_center {
  text-align: center;
}

#agautcviel .gt_left {
  text-align: left;
}

#agautcviel .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#agautcviel .gt_font_normal {
  font-weight: normal;
}

#agautcviel .gt_font_bold {
  font-weight: bold;
}

#agautcviel .gt_font_italic {
  font-style: italic;
}

#agautcviel .gt_super {
  font-size: 65%;
}

#agautcviel .gt_footnote_glyph {
  font-style: italic;
  font-size: 65%;
}
</style>

<div id="agautcviel" style="overflow-x:auto;">

<!--gt table start-->

<table class="gt_table">

<thead>

<tr>

<th colspan="3" class="gt_heading gt_title gt_font_normal gt_center">

DIAMONDS

</th>

</tr>

<tr>

<th colspan="3" class="gt_heading gt_subtitle gt_font_normal gt_center gt_bottom_border">

Prices of 50,000 round cut diamonds

</th>

</tr>

</thead>

<tr>

<th class="gt_col_heading gt_left" rowspan="1" colspan="1">

Name

</th>

<th class="gt_col_heading gt_left" rowspan="1" colspan="1">

Type

</th>

<th class="gt_col_heading gt_left" rowspan="1" colspan="1">

Description

</th>

</tr>

<tbody class="gt_table_body">

<tr>

<td class="gt_row gt_left" style="font-style:italic;">

price

</td>

<td class="gt_row gt_left">

double

</td>

<td class="gt_row gt_left">

price in US dollars ($326 - $18,823)

</td>

</tr>

<tr>

<td class="gt_row gt_left gt_striped" style="font-style:italic;">

carat

</td>

<td class="gt_row gt_left gt_striped">

double

</td>

<td class="gt_row gt_left gt_striped">

weight of diamond (0.2 - 5.01)

</td>

</tr>

<tr>

<td class="gt_row gt_left" style="font-style:italic;">

cut

</td>

<td class="gt_row gt_left">

character

</td>

<td class="gt_row gt_left">

quality of the cut (Fair, Good, Very Good, Premium, Ideal)

</td>

</tr>

<tr>

<td class="gt_row gt_left gt_striped" style="font-style:italic;">

color

</td>

<td class="gt_row gt_left gt_striped">

character

</td>

<td class="gt_row gt_left gt_striped">

diamond color, from D (best) to J (worst)

</td>

</tr>

<tr>

<td class="gt_row gt_left" style="font-style:italic;">

clarity

</td>

<td class="gt_row gt_left">

character

</td>

<td class="gt_row gt_left">

a measurement of how clear the diamond is (I1 (worst), SI2, SI1, VS2,
VS1, VVS2, VVS1, IF (best))

</td>

</tr>

<tr>

<td class="gt_row gt_left gt_striped" style="font-style:italic;">

x

</td>

<td class="gt_row gt_left gt_striped">

double

</td>

<td class="gt_row gt_left gt_striped">

length in mm (0-10.74)

</td>

</tr>

<tr>

<td class="gt_row gt_left" style="font-style:italic;">

y

</td>

<td class="gt_row gt_left">

double

</td>

<td class="gt_row gt_left">

width in mm (0-58.9)

</td>

</tr>

<tr>

<td class="gt_row gt_left gt_striped" style="font-style:italic;">

z

</td>

<td class="gt_row gt_left gt_striped">

double

</td>

<td class="gt_row gt_left gt_striped">

depth in mm (0-31.8)

</td>

</tr>

<tr>

<td class="gt_row gt_left" style="font-style:italic;">

depth

</td>

<td class="gt_row gt_left">

double

</td>

<td class="gt_row gt_left">

total depth percentage = z / mean(x, y) = 2 \* z / (x + y) (43-79)

</td>

</tr>

<tr>

<td class="gt_row gt_left gt_striped" style="font-style:italic;">

table

</td>

<td class="gt_row gt_left gt_striped">

double

</td>

<td class="gt_row gt_left gt_striped">

width of top of diamond relative to widest point (43-95)

</td>

</tr>

</tbody>

<tfoot>

<tr>

<td colspan="4" class="gt_sourcenote">

www.google.com

</td>

</tr>

</tfoot>

</table>

<!--gt table end-->

</div>

<!--/html_preserve-->