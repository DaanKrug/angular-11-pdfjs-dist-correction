# angular-11-pdfjs-dist-correction

Angular 11 encountered compilation problems in 
pdfjs-dist lib. The problem basically is in the use 
of "?." and "??" operators.

This project store the original file and the 
modified file.

The purpose of this repository is to be a backup of the 
workaround developed.

## Problematic File
node_modules/pdfjs-dist/build/pdf.js (Aka named "pdf_original.js")

## Correction File
Aka named "pdf.js"

## Workaround solution
1 - Replace the file: 
node_modules/pdfjs-dist/build/pdf.js by the corrected file in this
repository.


2 - In your Module use imports as follow:
 
 
<code> 
import * as PDFJS                               from 'pdfjs-dist/build/pdf.js';


import * as PDFJS_WORKER                        from 'pdfjs-dist/build/pdf.worker.entry.js';
</code>

3 - Use as recommended, setting the "workerSrc" property


<code>
...


PDFJS.GlobalWorkerOptions.workerSrc = PDFJS_WORKER;


var PDFDocumentLoadingTask = PDFJS.getDocument(some_url);


...
</code>


## Warning: 
This solution was only tested in funcion of download a PDF from a URL 
and extract the text of this file.

It can be possible that you experiment some error, because of
operators substitutions not was tested at all in other functions.
Some substitutions could be changed some kind of the original 
verifications, making changes in original behavior conditions.