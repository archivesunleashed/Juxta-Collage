# Creating JUXTA Collages with Web Archive Images

<p align="center">
  <img src="https://user-images.githubusercontent.com/7362321/200403378-c4e76630-62c4-4f8c-bae5-52bef8810aff.png" alt="Example JUXTA Collage Using Web Archive Image Data" width="600">
</p>

Welcome! The following tutorial provides instructions for building an image collage using Juxta shell script and image information dataset generated through the Archives Research Compute Hub (ARCH) platform.


## Overview

Web archive data is a rich source for studying the recent past. Web archives preserve a variety of information formats, including the full text of websites to image and video information, to network links among websites in a collection, and as such, offer a plethora of opportunities to explore web archive data. 

The following tutorial will outline how to create a JUXTA collage using an image dataset generated through the [Archives Research Compute Hub (ARCH)](https://support.archive-it.org/hc/en-us/articles/360061122492-Introduction-to-the-Archive-It-Research-Services-Cloud). By transforming image data, researchers have an opportunity to explore a web archive collection interactively.

## What is Juxta?

Juxta is a shell script which generates a collage of images for display on a webpage. You can learn more about the Juxta script through its GitHub page: [https://github.com/tokee/juxta](https://github.com/tokee/juxta).

## Acknowledgements

We recognize the following work and contributions which have made this tutorial possible.

[Toke Eskildsen](https://github.com/tokee) is the primary developer and contributor of the juxta script. 

The following tutorial was collaboratively designed by [Nick Ruest](https://ruebot.net/) and [Samantha Fritz](https://github.com/SamFritz).

Google Collab notebooks were built by Nick Ruest, with datasets examples generated using the Archives Research Compute Hub (ARCH).

* * *

## Considerations

Web archive data tends to be quite large and often outpaces the capacity of local storage on your computer. You may want to consider working with dedicated storage (HDD, SSD) or servers.
 
This tutorial was created using macOS.

## Pre-requisites

To complete this tutorial, you will need three things:

* The ARCH “image information” derivative
* The “[imagemagick](https://imagemagick.org/script/download.php#macosx)” package. To check if it is installed, run `convert -v` in your console.
* The “[jq](https://stedolan.github.io/jq/)” package. To check if it is installed, run `jq` in your console.

On Mac OS, both imagemagick and jq can be installed using brew (`brew install imagemagick` and `brew install ghostscript` for imagemagick; and `brew install jq` for jq). 
