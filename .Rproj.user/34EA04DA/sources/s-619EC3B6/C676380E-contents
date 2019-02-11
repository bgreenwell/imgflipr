#' Get memes
#'
#' Gets a data frame of popular memes that may be captioned with the Imgflip
#' API. The size of this array and the order of memes may change at any time.
#'
#' @return A data frame with one row per meme.
#'
#' @export
#'
#' @examples
#' \dontrun{
#' memes <- get_memes()
#' id <- memes[memes$name == "Batman Slapping Robin", "id"]
#' id
#' }
get_memes <- function() {
  url <- "https://api.imgflip.com/get_memes"
  memes <- jsonlite::fromJSON(url)
  if (memes$success) {
    tibble::as_tibble(memes$data$memes)
  } else {
    stop("Unknown error.")  # make better later
  }
}
