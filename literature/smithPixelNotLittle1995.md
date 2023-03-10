---
title: "A Pixel is not a Little Square"
authors: "Alvy Ray Smith"
year: 1995
tags: []
---
# A Pixel is not a Little Square

- [Bibliography](#bibliography)
- [Notes](#notes)
- [Abstract](#abstract)
- [Reading Notes](#reading-notes)

## Bibliography


## Abstract
My purpose here is to, once and for all, rid the world of the misconception that a pixel is a little geometric square. This is not a religious issue. This is an issue that strikes right at the root of correct image (sprite) computing and the ability to correctly integrate (converge) the discrete and the continuous. The little square model is simply incorrect. It harms. It gets in the way. If you find yourself thinking that a pixel is a little square, please read this paper. I will have succeeded if you at least understand that you are using the model and why it is permissible in your case to do so (is it?). Everything I say about little squares and pixels in the 2D case applies equally well to little cubes and voxels in 3D. The generalization is straightforward, so I won’t mention it from hereon1. I discuss why the little square model continues to dominate our collective minds. I show why it is wrong in general. I show when it is appropriate to use a little square in the context of a pixel. I propose a discrete to continuous mapping—because this is where the problem arises—that always works and does not assume too much.

## Notes
%% begin notes %%%% end notes %%
## Synopsis

[Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=1&annotation=undefined)“My purpose here is to […] rid the world of the misconception that a pixel is a little geometric square. […] This is an issue that strikes right at the root of correct image (sprite) computing and the ability to correctly integrate (converge) the discrete and the continuous. The little square model is simply incorrect.” ([Smith, p. 1](zotero://select/library/items/Y4ECLXWZ))

-   [Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=1&annotation=undefined)“The Little Square Model” ([Smith, p. 1](zotero://select/library/items/Y4ECLXWZ))
-   [Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=2&annotation=undefined)“So What Is a Pixel?” ([Smith, p. 2](zotero://select/library/items/Y4ECLXWZ))
-   [Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=6&annotation=undefined)“Why Is the Little square Model So Persistent?” ([Smith, p. 6](zotero://select/library/items/Y4ECLXWZ))
-   [Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=7&annotation=undefined)“How Does a Scanner Digitize a Picture?” ([Smith, p. 7](zotero://select/library/items/Y4ECLXWZ))
-   [Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=7&annotation=undefined)“How Does a Printer Print a Digital Image?” ([Smith, p. 7](zotero://select/library/items/Y4ECLXWZ))
-   [Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=8&annotation=undefined)“How Is an Image Displayed on a Monitor?” ([Smith, p. 8](zotero://select/library/items/Y4ECLXWZ))
-   [Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=9&annotation=undefined)“What Is a Discrete to Continuous Mapping That Works?” ([Smith, p. 9](zotero://select/library/items/Y4ECLXWZ))
-   [Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=9&annotation=undefined)“Image Broadening” ([Smith, p. 9](zotero://select/library/items/Y4ECLXWZ))
-   [Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=11&annotation=undefined)“Summary” ([Smith, p. 11](zotero://select/library/items/Y4ECLXWZ))

A pixel is a point in space rather then a little square. An image is then reconstructed from point samples, using different reconstruction filters. On of the poorest of these is the box filter. This on just applies a box to a point sample.

[Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=7&annotation=EK2FCNMZ)“When one “magnifies” or “zooms in on” an image in most popular applications, each pixel appears to be a little square. The higher the magnification or the closer in the zoom, the bigger the little squares get. Since I am apparently magnifying the pixel, it must be a little square, right? No, this is a false perception. What is happening when you zoom in is this: Each point sample is being replicated MxM times, for magnification factor M.” ([Smith, p. 7](zotero://select/library/items/Y4ECLXWZ))

## Glossary

-   [Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=1&annotation=undefined)“discrete to continuous mapping” ([Smith, p. 1](zotero://select/library/items/Y4ECLXWZ))
-   [Go to annotation](zotero://open-pdf/library/items/VYVH9UNL?page=2&annotation=undefined)“point sample” ([Smith, p. 2](zotero://select/library/items/Y4ECLXWZ))

## Related
%% begin related %%%% end related %%

%% Import Date: 2023-03-10T15:47:57.231+01:00 %%
