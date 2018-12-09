---
layout: lesson
target-tutorial: book-digitization
title: "Unit 3: Optical character recognition and finalization of e-book file"
authors: Tomislav Medak, Dubravka Sekulić, An Mertens
---

## IV. Optical character recognition

Before the edited-down image files are finalized as an e-book, we want to transform the image of the text into an actual text that can be searched, highlighted, copied and transformed. That functionality is provided by Optical Character Recognition. This a technically difficult task - dependent on language, script, typeface and quality of print - and there aren't that many OCR tools that are good at it. There is, however, a relatively good free software solution - [Tesseract](http://code.google.com/p/tesseract-ocr/) - that has solid performance, good language data and can be trained for an even better performance, although it has its problems. Tesseract is a command line tool, but there are a number of GUI tools that integrate Tesseract, Gscan2PDF on GNU/Linux being our favorite. Proprietary solutions (e.g. Abbyy FineReader or Adobe Acrobat Professional) sometimes have superior results, a greater latitude of languages and scripts, and a better workflow integration.

Tesseract supports as input format primarily .tiff files. It produces a plain text file that can, with the help of other tools, be embedded as a separate text layer under or above the original image of the text in a PDF file.

With the help of other tools, OCR can be performed also against other input file types, such as graphic-only PDF files. This produces inferior results, depending again on the quality of images files and the reproduction of text in them. One such tool is a bashscript to OCR an ODF file that can be found at the [GitHub ocr.sh reposotory](https://github.com/andrecastro0o/ocr/blob/master/ocr.sh).

As mentioned in the 'before scanning' section, the quality of the original book will influence the quality of the scan and thus the quality of the OCR. For a comparison, have a look at [the results of tests here](http://www.paramoulipist.be/?p=1303).

Once you have your plaintext extraction, there is still some work to be done. Because OCR has difficulties to interpret particular elements in the lay-out and fonts, the TXT file can have a lot of errors. Most GUIs will allow you to edit the text layer before you finalize the e-book file.

Recurrent problems are:
- combinations of specific letters in some fonts (it can mistake 'm' for 'n' or 'I' for 'i' etc.);
- headers become part of body text;
- footnotes are placed inside the body text;
- page numbers are not recognized as such.

## V. Finalizing an e-book file

After the optical character recognition has been completed, the resulting text can be merged with output into an e-book format. While the e-book file formats such as ePub have gained ground, PDFs still remain popular because many people tend to read on their computers, and they retain the original layout of the book on paper, including the absolute pagination needed for referencing in citations. DjVu is also an option, as an alternative to PDF, used because of its purported superiority, but it is far less popular.

The export to PDF can be done again with a number of tools. In our case, we'll complete the optical character recognition and PDF export in gscan2pdf. The proprietary Abbyy FineReader will produce a bit smaller PDFs.

If you prefer to use an e-book format that works better with e-book readers, obviously you will have to remove some of the elements that appear in the book - headers, footers, footnotes and pagination – that are specific to the layout of the book. This can be done earlier in the process of cropping down the original .jpg image files (see under III) and then outputting the OCR text as an .doc, .epub or .mobi file. It can also be done from the finalized PDF by converting the PDF in the [Calibre e-book management tool](http://calibre-ebook.com) into an .epub or .mobi file. The process and result will be though quite messy.

1. Optical character recognition and PDF export in MOTW workflow

Optical character recognition with the Tesseract engine can be performed on GNU/Linux by a number of command line and GUI tools. Much of those tools exist also for other operating systems. For the users of the Public Library workflow, we recommend using gscan2pdf application both for the optical character recognition and the PDF or DjVu export.

To do so, start gscan2pdf and open your .tiff files. To OCR them, go to 'Tools' and select 'OCR'. In the dialog box select the Tesseract engine and your language. 'Start OCR'. Once the OCR is finished, export the text image files and the OCR text to PDF by selecting 'Save as'.

However, given that sometimes the proprietary solutions produce better results, these tasks can also be done, for instance, on the Abbyy FineReader running on a Windows operating system running inside the Virtual Box. The prerequisites are that you have both Windows and Abbyy FineReader you can install in the Virtual Box. If using Virtual Box, once you've got both installed, you need to designate a shared folder in your Virtual Box and place the .tiff files there. You can now open them from the Abbyy FineReader running in the Virtual Box, OCR them and export them into a PDF.

To use Abbyy FineReader transfer the output files in your 'out' out folder to the shared folder of the VirtualBox. Then start the VirtualBox, start Windows image and in Windows start Abbyy FineReader. Open the files and let the Abbyy FineReader read the files. Once it's done, output the result into PDF.

## VI. Cataloging and sharing the e-book

Your journey from a printed book on paper to an e-book now finished. If you want to maintain your library you can use Calibre, a free software tool for e-book library management. You can add the metadata to your book using the existing catalogs or you can enter metadata manually.

Now you may want to distribute your book. If the work you've digitized is in the [public domain](https://en.wikipedia.org/wiki/Public_domain), you might consider contributing it to the [Gutenberg project](http://www.gutenberg.org/wiki/Gutenberg:Volunteers'_FAQ#V.1._How_do_I_get_started_as_a_Project_Gutenberg_volunteer.3F ), [Wikibooks](https://en.wikibooks.org/wiki/Help:Contributing ) or [Internet Archive](http://archive.org).

If the work is still under copyright, you might explore a number of different options for sharing.
