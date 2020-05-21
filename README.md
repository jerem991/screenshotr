##### Forked from https://github.com/dynamicnet/screenshotr

# Screenshot and PDF converter

Dockerized node webservice that take screenshot of webpage or convert it to PDF

```
# Launch Container
# The http service will listen on 127.0.0.1 on port 3000
docker run -p 3000:3000 -d jerem991/screenshotr

# Take a screenshot of GitHub homepage
curl http://127.0.0.1:3000/screenshot?url=https://github.com/ > github-home.png

# Convert GitHub homepage to PDF
curl http://127.0.0.1:3000/pdf?url=https://github.com/ > github.pdf
```


## Parameters
### endpoint /screenshot
Name | Type | Description
---- | ---- | -----------
url | required string | url of the page to screenshot
vp_width | opt. int | set the viewport width in pixel. Defaults to 1024
vp_height | opt. int | set the viewport height in pixel. Defaults to 768
o_width | opt. int | set the width of the returned image. Default to the viewport width
o_height | opt. int | set the height of the returned image. Default to the viewport height
o_format | opt. string (png\|jpg) | set image format for the returned image. Defaults to png
dom_element_selector | opt. string | a CSS selector of the element you want to screenshot, only if you don't want to screenshot the entire page
fullpage | opt. int (0\|1) | "1" to take a screenshot of the fullpage, "0" to take a screenshot of the viewport only. Default to 1

### endpoint /pdf
Name | Type | Description
---- | ---- | -----------
url | required string | url of the page to screenshot
scale | opt. float | Scale of the webpage rendering. Defaults to 1. Scale amount must be between 0.1 and 2.
printBackground | opt. bool | Print background graphics. Defaults to false.
landscape | opt. bool | Paper orientation. Defaults to false.
format | opt. string | Paper format. Defaults to 'A4'.
delay | opt. int | Wait some time (in milliseconds) before converting. Defaults to 0.
pageRanges | opt. string | Paper ranges to print, e.g., '1-5, 8, 11-13'. Defaults to the empty string, which means print all pages.
