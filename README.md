page_dewarp

---

This fork optimizes the original code through several key changes resulting in approximately a 30x speed-up while retaining comparable output quality:
* Using BFGS over Powell
* Reducing the number of spans used
    * This results in a smaller number of parameters requiring optimization
    * Selecting a few spans in an informed way is _usually_ sufficient to capture the dewarped nature
    * Warping profile (i.e., z-displacement as the x-axis is traversed) should be largely the same for most spans
    * Seven (7) spans are selected:
        * Top two spans
        * Three equidistant middle spans
        * Two bottom spans
    * The seven spans are usually adequate to capture the z-displacement _and_ other potential image deformations (e.g., rotated pages, fisheye effects, etc)
* Decreasing the decimate factor

---

Page dewarping and thresholding using a "cubic sheet" model - see full writeup at <https://mzucker.github.io/2016/08/15/page-dewarping.html>

Requirements:

 - scipy
 - OpenCV 3.0 or greater
 - Image module from PIL or Pillow
 
Usage:

    page_dewarp.py IMAGE1 [IMAGE2 ...]
