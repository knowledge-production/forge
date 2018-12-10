---
layout: lesson
target-tutorial: book-digitization
title: "Unit 3: Post-processing"
authors: Tomislav Medak, Dubravka Sekulić, An Mertens
---

## II. Preparing the Image Files for Post-Processing

Once the book pages have been captured, they have to be transferred to the computer and prepared for post-processing. If you use a flatbed or a photocopier, whatever application you use to operate the scanner (e.g. Xsane on GNU/Linux, Windows or Mac OSX) capture pages preferably as separate images. Capturing a book on a flatbed or a photocopier will take longer than the overhead camera setup, but it you’ll have photos ready for post-processing.

With two-camera scanners, the capturing process will result in two separate sets of images -- odd and even pages -- coming from the left and the right camera respectively -- and you will need to rename and reorder them accordingly, rotate them into a vertical orientation and collate them into a single sequence of files.

### a) Transferring image files

For the transfer of files your principal choices are either to copy the files by removing the memory cards from the cameras and copying them to the computer via a card reader - or to transfer them via a USB cable. The latter process can be automated by remote operating your cameras from a computer, however this can be done only with a certain number of Canon cameras (http://bit.ly/16xhJ6b) that can be hacked to run the open Canon Hack Development Kit firmware (http://chdk.wikia.com).

After transferring the files, you want to erase all the image files from the camera memory card, so that they would not end up messing up the scan of the next book.

### b) Renaming image files

As the left and the right camera are typically operated in sync, the photographing process results in two separate sets of images, with even and odd pages respectively, that have completely different file names and potentially same time stamps. So before you collate the page images in the order how they appear in the book, you want to rename the files so that the first image comes from the right camera, the second from the left camera, the third comes again from the right camera and so on. You probably want to do a batch renaming, where your right camera files start with n and are offset by an increment of 2 (e.g. page_0000.jpg, page_0002.jpg,...) and your left camera files start with n+1 and are also offset by an increment of 2 (e.g. page_0001.jpg, page_0003.jpg,...).

Batch renaming can be completed either from your file manager, in command line or with a number of GUI applications (e.g. GPrename, rename, cuteRenamer on GNU/Linux).

### c) Rotating image files

Before you collate the renamed files, you might want to rotate them. This is a step that can be done also later in the post-processing (see below), but if you are automating or scripting your steps this is a practical place to do it. The images leaving your cameras will be positioned horizontally. In order to position them vertically, the images from the camera on the right will have to be rotated by 90 degrees counter-clockwise, the images from the camera on the left will have to be rotated by 90 degrees clockwise.

Batch rotating can be completed in a number of photo-processing tools, in command line or dedicated applications (e.g. Fstop, ImageMagick, Nautilus Image Converter on GNU/Linux).

### d) Collating images into a single batch

Once you're done with the renaming and rotating of the files, you want to collate them into the same folder for easier manipulation later.

Getting the image files ready for post-processing on the MOTW scanner

In the case of MOTW scanner, a custom C++ script was written by Mislav Stublić to facilitate the transfer, renaming, rotating and collating of the images from the two cameras.

The script prompts the user to place into a card reader connected to the computer first the memory card from the right camera, provides a preview of the first and last four images and provides an entry field to create a sub-folder in a local cloud storage folder (path: /home/[username]/Copy). It transfers, renames, rotates the files, deletes them from the card and prompts the user to replace the card with the one from the left camera in order to the transfer the files that card and place them in the same folder. The script was created for GNU/Linux system and it can be downloaded, together with its source code, from [here](/forge/public/files/scanflow_script-source_and_binary.zip).

If you have other cameras than Canon, you can edit the line 387 of the source file to change to the naming convention of your cameras, and recompile by running the following command in your terminal: "gcc scanflow_en.c -o scanflow_en -ludev `pkg-config --cflags --libs gtk+-2.0`".

## Transformation of source images into .tiff files

Images transferred from the cameras are high definition full-color images. You want your cameras to shoot at the largest possible .jpg resolution in order for resulting files to have at least 300 dpi (A4 at 300 dpi requires a 9.5 megapixel image). In the post-processing the size of the image files needs to be reduced down radically, so that several hundred images can be merged into an e-book file of a tolerable size. Images from a flatbed or photocopier will have to be cropped and converted too.

Hence, the first step in the post-processing is to crop the images only to the content of the pages. The surroundings around the book that were captured in the image and the white margins of the page will be cropped away, while the printed text will be transformed into a monochrome text. The illustrations, however, will need to be preserved in their color form, and mixed with the black and white text. What were initially large .jpg files will now become relatively small .tiff files that are ready for optical character recognition process (OCR).

These tasks can be completed by a number of software applications. Our tutorial will focus on one that can be used across all major operating systems -- ScanTailor. The latest ScanTailor Advanced can be downloaded from [its GitHub repository](https://github.com/4lex4/scantailor-advanced/releases/). For an older version of ScanTailor existing in builds for GNU/Linux and Mac OSX as well, see the [ScanTailor Classic repository](https://github.com/scantailor/scantailor/wiki/User-Guide). A detailed video tutorial of ScanTailor can be found on [Vimeo](http://vimeo.com/12524529).

### ScanTailor: from a photograph of a page to an image file ready for optical character recognition

Once you have transferred all the photos from cameras to the computer, renamed and rotated them, or captured them on a flatbed or a photocopier, they are ready to be processed in the ScanTailor.

![ScanTailor Advanced](/forge/public/images/book-digitization/ScanTailor_advanced.png)

### 1. Importing images to ScanTailor

- start ScanTailor and open ‘new project’
- for ‘input directory’ chose the folder where you stored the transferred and renamed photographs or scanner images
- you can leave ‘output directory’ as it is, it will place your resulting .tiffs in an 'out' folder inside the folder where your .jpg images are
- select all files (if you followed the naming convention above, they will be named ‘page_xxxx.jpg’) in the folder where you stored the transferred photo images, and click 'OK'
- in the dialog box ‘Fix DPI’ click on All Pages, and for DPI choose preferably '600x600', click 'Apply', and then 'OK' (we want to preserve as large resolution as possible for the optical character recognition)

### 2. Editing pages

#### 2.1 Rotating photos/pages
If you've rotated the photo images in the previous step using the scanflow script, skip this step – otherwise:
- under the ‘Filters’ pane, select ‘Fix Orientation, rotate the first photo, click Apply and for scope select ‘Every other page’ followed by 'OK'
- if you have used a two-camera scanner, rotate the following photo in the opposite direction and again apply it to ‘Every other page’

#### 2.2 Deleting redundant photographs/pages
- remove redundant pages (photographs of the empty cradle at the beginning and the end of the book scanning sequence; book cover pages if you don’t want them in the final scan; duplicate pages etc.) by right-clicking on a thumbnail of that page in the Thumbnail pane on the right, selecting ‘Remove from project’ and confirming by clicking on ‘Remove’.

> If you by accident remove a wrong page, you can re-insert it by right-clicking on a page before/after the missing page in the sequence, selecting 'insert after/before' (depending on which page you selected) and choosing the file from the list. Before you finish adding, it is necessary to again go through the procedure of fixing DPI and Rotating for the images you have added.

#### 2.3 Adding missing pages
- If you notice that some pages are missing, you can recapture and insert them manually at this point using the procedure described above under 2.2.

### 3. Split pages and deskew
Steps ‘Split pages’ and ‘Deskew’ in the ‘Filter’ pane should work automatically. Run them by clicking the ‘Play’ button under the 'Select content' function. This will do the three steps automatically: splitting of pages, deskewing and selection of content. After this, you can manually re-adjust splitting of pages and de-skewing.

### 4. Selecting content
Step ‘Select content’ works automatically as well, but it is important to revise the resulting selection manually page by page to make sure the entire content is selected on each page (including the header and page number). Where necessary, use your pointer device to adjust the content selection.

If the inner margin is cut, go back to 'Split pages' view and manually adjust the selected split area. If the page is skewed, go back to 'Deskew' and adjust the skew of the page. After this go back to 'Select content' and readjust the selection if necessary.

This is the step where you do visual control of each page. Make sure all pages are there and selections are as equally distant from the top and bottom, left and right margins.

At the bottom of the thumbnail column there is a sort option that can automatically arrange pages by height and width of the selected content, making the process of manual selection easier. The selections should be equidistant from the top and bottom, left and right margins, but need not cover the full page. The exception should be cover and back pages where we advise to select the full page.

### 5. Adjusting margins
For best results select in the previous step content of the full cover and back page. Now go to the 'Margins' step and set under Margins section both Top, Bottom, Left and Right to 0.0 and do 'Apply to...' → 'All pages'.

In Alignment section leave 'Match size with other pages' ticked, choose the central positioning of the page and do  'Apply to...' → 'All pages'. This will make each page centered on the center of the selected content. For this reason, we want selections that are equidistant from the top and the bottom, the left and the right margins.

### 6. Outputting the .tiffs
Now go to the 'Output' step. Ignore the 'Output Resolution' section.

Next, review pages from the middle of the book to see if the scanned text is too faint or too dark. If the text seems too faint or too dark, use slider Thinner – Thicker to adjust. Do 'Apply to' → 'All pages'.

Next, go to the cover page and select under Mode 'Color / Grayscale' and tick on 'Cut Margins’ (‘White Margins' in older versions of ScanTailor). Do the same for the back page.

If there are pages with illustrations, you can choose the 'Mixed' mode for those pages, select under ‘Picture shape’ ‘Rectangular’, and then under the thumb 'Picture Zones' adjust the zones of the illustrations.

Now you are ready to output the files. Just press the 'Play' button under 'Output'. Once the computer is finished processing the images, just do 'File' → 'Save as' to save the project.
