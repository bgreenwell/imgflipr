
<!-- README.md is generated from README.Rmd. Please edit that file -->

# imgflipr

The goal of imgflipr is to, you guessed it, interact with the official
[Imgflip API](https://api.imgflip.com/) through R. For making custom
memes, check out the R 📦 [meme](https://github.com/GuangchuangYu/meme/).

## Installation

Currently, you can only install this package from GitHub:

``` r
devtools::install_github("bgreenwell/imgflipr")
```

## Example

Grab a tibble of the most popular memes:

``` r
memes <- imgflipr::get_memes()
memes
#> # A tibble: 100 x 5
#>    id        name                  url                         width height
#>  * <chr>     <chr>                 <chr>                       <int>  <int>
#>  1 112126428 Distracted Boyfriend  https://i.imgflip.com/1ur9…  1200    800
#>  2 87743020  Two Buttons           https://i.imgflip.com/1g8m…   600    908
#>  3 155067746 Surprised Pikachu     https://i.imgflip.com/2kbn…  1893   1893
#>  4 102156234 Mocking Spongebob     https://i.imgflip.com/1otk…   502    353
#>  5 93895088  Expanding Brain       https://i.imgflip.com/1jwh…   857   1202
#>  6 124822590 Left Exit 12 Off Ramp https://i.imgflip.com/22bd…   804    767
#>  7 438680    Batman Slapping Robin https://i.imgflip.com/9ehk…   400    387
#>  8 119139145 Blank Nut Button      https://i.imgflip.com/1yxk…   600    446
#>  9 89370399  Roll Safe Think Abou… https://i.imgflip.com/1h7i…   702    395
#> 10 4087833   Waiting Skeleton      https://i.imgflip.com/2fm6…   298    403
#> # ... with 90 more rows
```

Grab the ID for a particular image:

``` r
batman <- memes[memes$name == "Batman Slapping Robin", "id"]
```

Caption this image (note, I have my [Imgflip](https://imgflip.com/)
username and password stored as an environment variable in my
`.Renviron` file):

``` r
url <- imgflipr::caption_image(
  template_id = batman, 
  username = Sys.getenv("IMGFLIP_USERNAME"), 
  password = Sys.getenv("IMGFLIP_PASSWORD"), 
  text0 = "Damn it, Robin",
  browse = FALSE  # don't open the captioned image in a browser
)
url
#> [1] "https://i.imgflip.com/2tfcto.jpg"
```

For now, just visit the link to your captioned image, it’s that easy\!
Alternatively, you can include the captioned image in R markdown by
passing the resulting URL to
`knitr::include_graphics()`:

``` r
knitr::include_graphics(url)
```

<img src="https://i.imgflip.com/2tfcto.jpg" width="50%" style="display: block; margin: auto;" />
