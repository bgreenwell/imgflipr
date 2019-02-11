#' Caption image
#'
#' Add a caption to an Imgflip meme template. Images created with this API will
#' be publicly accessible by anyone through the url in the response - there is
#' no "private" option. This does not mean these memes will be posted publicly
#' though, one still needs to know the exact URL to find the image. If the image
#' hangs around on Imgflip servers for a while and gets very few views (direct
#' image views and image page views both count), it will be auto-deleted to save
#' space.
#'
#' @param template_id Character string specifying a template ID as returned by
#' the \code{get_memes} function. Any ID that was ever returned from the
#' \code{get_memes} response should work for this parameter.
#'
#' @param username Character string specifying a username of a valid imgflip
#' account. This is used to track where API requests are coming from.
#'
#' @param password Character string specifying the password for the imgflip
#' account.
#'
#' @param text0 Character string specifying the top text for the meme.
#'
#' @param text1 Character string specifying the bottom text for the meme.
#'
#' @param font Character string specifying the font family to use for the text.
#'
#' @param max_font_size Character string specifying the maximum font size in
#' pixels. Defaults to \code{"50"} (for 50px).
#'
#' @param browse Logical indicating whether to open the resulting URL
#' (\code{TRUE}) or just return the link (\code{FALSE}). Default is \code{TRUE}.
#'
#' @return The URL to the generated meme.
#'
#' @export
#'
#' @examples
#' \dontrun{
#' memes <- get_memes()
#' id <- memes[memes$name == "Batman Slapping Robin", "id"]
#' caption_image(id, username = "", password = "", text0 = "Damn it, Robin",
#'               browse = TRUE)
#' }
caption_image <- function(
  template_id,
  username,
  password,
  text0 = "",
  text1 = "",
  font = "impact",
  max_font_size = "50",
  browse = FALSE
) {
  res <- httr::POST(
    url = "https://api.imgflip.com/caption_image",
    body = list(
      template_id = template_id,
      username =  username,
      password =  password,
      text0 = text0,
      text1 = text1,
      font = font,
      max_font_size = max_font_size
    ),
    #httr::verbose(),
    encode = "form"
  )
  parsed <- httr::content(res, as = "parsed")
  if (browse) {
    utils::browseURL(parsed$url)
  } else {
    parsed$url
  }
}
