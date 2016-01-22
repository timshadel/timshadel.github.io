---
title: PDF printer
author: Tim
layout: post
permalink: /2005/01/25/pdf-printer/
categories:
  - Impressions
tags:
  - acrobat
  - pdf printer
  - primopdf
  - Tools
---
I find it really convenient to turn many of my documents into PDF. It lets me easily send stuff to people that don&#8217;t have a particular program, like a [UML diagramming tool][1]. I&#8217;ve poked around for the last little while, and these are the most useful solutions I&#8217;ve come across:

  * [Adobe Acrobat][2]. Obviously this is the most *authoritative* source of creating PDF files. I used Acrobat at two different companies. Acrobat has two options: Acrobat Writer and Acrobat Distiller. As I understand it, Distiller is better for complex documents. I never really needed anything but Writer. Personally, I don&#8217;t want to pay to create PDF files, and my needs are simple, so I&#8217;ve always skipped this option for personal use.
  * [OpenOffice][3]. This is the famous open source word processing suite. There&#8217;s a button for &#8220;Export to PDF&#8221;. It&#8217;s easy to use, but it&#8217;s pretty heavyweight to install if all you want is to turn your TXT file into a PDF document.
  * [PDF995][4]. This is a very simple, and easy to use PDF creation tool. It looks like a printer, so anything you can print you can make into a PDF. It&#8217;s supported by ads, so each time you print a browser opens to an ad. My biggest annoyance with this is that it would sometimes change my receipt page into an ad. If anything out of the ordinary happened (USB keychain not plugged in, network permissions wrong), then I lost my receipt. Besides that, it was good quality. Just ad-supported.
  * [PDFCreator][5]. This is an open source PDF converter that I ran into just the other day. It appears to act as a PostScript printer, and then rely on a PS2PDF converter like [GhostView][6] to finish the conversion process to PDF. I never actually got a PDF out of this, but many people reported being able to set it up on a central server as a network printer and have a way that anyone in the organization could create PDFs. It was more complex than I wanted.
  * [PrimoPDF][7]. I just found this one tonight. It seems like the ideal solution. It&#8217;s completely free to use. It&#8217;s simple, and is just a printer, like PDF995. It also allows you to optimize the PDF for either screen or print. I don&#8217;t know what the difference is . I&#8217;m also not sure how output differs from PDF995, but here are two samples. Both are of [this web page][8]. One is [optimized for screen][9] and the other is [optimized for print][10].

 [1]: http://www.sparxsystems.com.au/ea.htm "Enterprise Architect"
 [2]: http://www.adobe.com/products/acrobatstd/main.html
 [3]: http://www.openoffice.org/
 [4]: http://www.pdf995.com/
 [5]: http://pdfcreator.sourceforge.net/
 [6]: http://www.cs.wisc.edu/~ghost/
 [7]: http://www.primopdf.com
 [8]: http://www.sparxsystems.com.au/ea.htm "Enterprise Architect modeling tool"
 [9]: http://timshadel.com/blog/files/eascreen.pdf "Screen optimized sample PDF"
 [10]: http://timshadel.com/blog/files/eaprint.pdf "Print optimized sample PDF"
