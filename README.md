# Creating JUXTA Collages with Web Archive Images

<p align="center">
  <img src="https://user-images.githubusercontent.com/7362321/200403378-c4e76630-62c4-4f8c-bae5-52bef8810aff.png" alt="Example JUXTA Collage Using Web Archive Image Data" width="600">
</p>

Welcome! The following tutorial provides instructions for building an image collage using Juxta shell script and image information dataset generated through the Archives Research Compute Hub (ARCH) platform.

# Table of Contents
- [Overview](https://github.com/archivesunleashed/Juxta-Collage##overview)
- [What is a Juxta?](https://github.com/archivesunleashed/Juxta-Collage##whatisajuxta)
- [Considerations](https://github.com/archivesunleashed/Juxta-Collage##considerations)
- [Pre-requisites](https://github.com/archivesunleashed/Juxta-Collage##Pre-requisites)
- [Creating a JUXTA Image Collage](https://github.com/archivesunleashed/Juxta-Collage#creating-a-juxta-image-collage)
  - [1. ARCH - Run image information job](https://github.com/archivesunleashed/Juxta-Collage#1-arch---run-image-information-job)
  - [2. Copy the derivative URL](https://github.com/archivesunleashed/Juxta-Collage#2-copy-the-derivative-url)
  - [3. Working with Google Collab Notebook](https://github.com/archivesunleashed/Juxta-Collage#3-working-with-google-collab-notebook)
  - [4. Clone Juxta](https://github.com/archivesunleashed/Juxta-Collage#4-clone-juxta)
  - [5. Create .dat file](https://github.com/archivesunleashed/Juxta-Collage#5-create-dat-file)
  - [6. Create JUXTA files](https://github.com/archivesunleashed/Juxta-Collage#6-create-juxta-files)
  - [7. Launch Local Server](https://github.com/archivesunleashed/Juxta-Collage#7-launch-local-server)

## Acknowledgements

We recognize the following work and contributions which have made this tutorial possible.

[Toke Eskildsen](https://github.com/tokee) is the primary developer and contributor of the juxta script. 

The following tutorial was collaboratively designed by [Nick Ruest](https://ruebot.net/) and [Samantha Fritz](https://github.com/SamFritz).

Google Collab notebooks were built by Nick Ruest, with datasets examples generated using the Archives Research Compute Hub (ARCH).

* * *

## Overview

Web archive data is a rich source for studying the recent past. Web archives preserve a variety of information formats, including the full text of websites to image and video information, to network links among websites in a collection, and as such, offer a plethora of opportunities to explore web archive data. 

The following tutorial will outline how to create a JUXTA collage using an image dataset generated through the [Archives Research Compute Hub (ARCH)](https://support.archive-it.org/hc/en-us/articles/360061122492-Introduction-to-the-Archive-It-Research-Services-Cloud). By transforming image data, researchers have an opportunity to explore a web archive collection interactively.

## What is Juxta?

Juxta is a shell script which generates a collage of images for display on a webpage. You can learn more about the Juxta script through its GitHub page: [https://github.com/tokee/juxta](https://github.com/tokee/juxta).

## Considerations

Web archive data tends to be quite large and often outpaces the capacity of local storage on your computer. You may want to consider working with dedicated storage (HDD, SSD) or servers.
 
This tutorial was created using macOS.

## Pre-requisites

To complete this tutorial, you will need three things:

* The ARCH “image information” derivative
* The “[imagemagick](https://imagemagick.org/script/download.php#macosx)” package. To check if it is installed, run `convert -v` in your console.
* The “[jq](https://stedolan.github.io/jq/)” package. To check if it is installed, run `jq` in your console.

On Mac OS, both imagemagick and jq can be installed using brew
* `brew install imagemagick` and `brew install ghostscript` for imagemagick
* `brew install jq` for jq

<p align="right">
  <a href="https://github.com/archivesunleashed/Juxta-Collage/edit/main/README.md#table-of-contents"><b>Back to ToC</b></a>
</p>

* * *

# Creating a JUXTA Image Collage

## 1. ARCH - Run image information job

Within ARCH, select a collection, and generate a new dataset from the file formats category called extract image information.

[insert video here]

<p align="right">
  <a href="https://github.com/archivesunleashed/Juxta-Collage/edit/main/README.md#table-of-contents"><b>Back to ToC</b></a>
</p>

## 2. Copy the derivative URL

On the dataset summary page, right-click on the download icon and select “copy link.” This will be the derivate URL needed for working with images in the Notebook.

[insert video here]

<p align="center">
  <img src="https://user-images.githubusercontent.com/7362321/200409026-8016b6a8-f6be-4534-8732-35a38a05d440.png" alt="Right click on download to copy dataset URL within ARCH" width="600">
</p>

<p align="right">
  <a href="https://github.com/archivesunleashed/Juxta-Collage/edit/main/README.md#table-of-contents"><b>Back to ToC</b></a>
</p>

## 3. Working with Google Collab Notebook

Create a copy of the notebook: https://colab.research.google.com/drive/14tlccAWkvTwy5dDYNlUhmN2hkMV1rxPj?usp=sharing

[insert video here]

Working from the copied notebook now, you will start off by changing the title. You may find it easiest to note the collection number in the title if you plan to work with multiple copies of the template. 

There are a few cells that will need a change in information.

First, change the URL listed in the first cell to the URL of the image information datasets (step 3). The curl command is used to **transfer data to and from a server**. In this case, the notebook calls out to the extracted image information dataset from ARCH. 

In cell six, which identifies the Wayback URL, change the collection id to match the collection we are currently working with.

Finally, in the last cell change the collection id in the CSV title. This title could be anything that’s meaningful to you as a researcher, but we do suggest maintaining consistency by using the collection id.

[insert video here]

Located at the top, click on the **Runtime** menu and select **Run All**. Alternatively, you can manually click on each play button. The pre-scripted actions in this notebook will ultimately generate a .txt file with formatted image URLs, which can then be used to fetch and download the images from this web archive collection using a single command line function.

[insert video here]

In the right-hand pane, which is collapsed by default, click on the file folder icon and download the **.txt** file to either your desktop or a server.

[insert video here]

Create a directory (folder) to house the recently downloaded .txt file. For this example, a directory called **13709Juxta** was created on a local desktop.

Next, create a subfolder in the new directory and call it **images**.

Our example path to our main working directory looks like this:
`/Users/fritz/Desktop/13709Juxta`

Using your terminal window, navigate to the images directory. Then use the following command to download all the images from the text file to the images folder. This directory of images is what will be used to create the Juxta collage.

`wget --random-wait -i ../13709_image_urls.txt`

> NOTE: Downloading the images will take time! Do not close your terminal window.

<p align="right">
  <a href="https://github.com/archivesunleashed/Juxta-Collage/edit/main/README.md#table-of-contents"><b>Back to ToC</b></a>
</p>

## 4. Clone Juxta

Navigate to [https://github.com/tokee/juxta](https://github.com/tokee/juxta). Use the URL provided under the Code Tab to clone. 

Clone Juxta within your main directory by using the following command

`Git clone https://github.com/tokee/juxta.git`

Note your path to Juxta; for simplicity's sake in this example, we’ve cloned JUXTA to our main working directory `/Users/fritz/Desktop/13709Juxta`

<p align="right">
  <a href="https://github.com/archivesunleashed/Juxta-Collage/edit/main/README.md#table-of-contents"><b>Back to ToC</b></a>
</p>

## 5. Create .dat file

A **.dat** file is a “generic data file that contains important information about the program used to create the particular file.” For the purposes of generating a JUXTA image collage, we will be converting the jpg image files downloaded from the replay URLs and redirecting the output as a .dat file format.

From your terminal, navigate to be one directory above where the images are saved.

For instance:		`/Users/fritz/Desktop/13709Juxta`

Run the following command to find the images and redirect the output to a .dat file

`find images > images.dat`

<p align="right">
  <a href="https://github.com/archivesunleashed/Juxta-Collage/edit/main/README.md#table-of-contents"><b>Back to ToC</b></a>
</p>

## 6. Create JUXTA files

Next, we are going to create all of the juxta files and tiles needed to view in a web browser. 

We are creating a new directory for all of the JUXTA files. You will need to make a few modifications to the command below: 

`THREADS=4 /Users/fritz/Desktop/13709Juxta/juxta/juxta.sh images.dat example`

Here’s a quick breakdown of what this line of code does:

|                                 |                                                                                                                                                                                                                                                                                                    |
|---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `THREADS=4`                       | You may need to change the number of threads. This example opts for four threads, with a total of 8 cores available. As this tutorial uses local computer storage, changing the threads ultimately means the laptop is used for processing JUXTA files but can continue to be used for other work. |
| `/Users/fritz/Desktop/13709Juxta` | Change to the path of where you’ve cloned Jutxa.                                                                                                                                                                                                                                                   |
| `example`                         | This will be the name of the directory in which Juxta formatted files are created. You can change this to whatever makes sense for you, but be sure to avoid spaces.                                                                                                                               |

Before launching a local server, navigate to the example directory created with the command above.

`cd example`

<p align="right">
  <a href="https://github.com/archivesunleashed/Juxta-Collage/edit/main/README.md#table-of-contents"><b>Back to ToC</b></a>
</p>

## 7. Launch Local Server

Now that all the JUXTA files have been created we will use Python to serve files from a local directory via HTTP. This will allow you to display and explore the image collage through the web browser.

`python3 -m http.server`

To launch the server, enter the local host address as a URL.

`Localhost:8000`

<p align="right">
  <a href="https://github.com/archivesunleashed/Juxta-Collage/edit/main/README.md#table-of-contents"><b>Back to ToC</b></a>
</p>
