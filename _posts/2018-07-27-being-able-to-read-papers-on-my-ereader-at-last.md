---
layout: post
title: Being able to read papers on my e-reader, at last
date: 2018-07-27T20:28:43+02:00
---

I truly wonder why papers are still made available as PDF documents on the Internet, rather than HTML pages. And moreover, why are they almost all formatted with a 2-columns layout? It makes them easy to read on a desktop screen, and I must admit quite nice looking, but the (huge) downside is that they are almost unreadable on an e-reader or a mobile phone screen, and that’s a pain considered that most of them are quite long, and demand a sustained focused effort to digest them.

But luckily, thanks to [this awesome repository of haskell papers reformatted to be read on an e-reader](https://github.com/beerendlauwers/haskell-papers-ereader), I just discovered the awesome [k2pdfoptlib](http://willus.com/k2pdfopt/) utility, which optimizes PDF/DJVU files for mobile e-readers and smartphones.

And I have to admit that it works well!

![Build Systems à la Carte optimized for a Kobo Glo](/images/being-able-to-read-papers-on-my-ereader-at-last-1.jpg)

To install _k2pdfoptlib_, just download it from [willus.com/k2pdfopt/download/](http://willus.com/k2pdfopt/download/), and drop the `k2pdfopt` binary file somewhere in your path (for example `/usr/local/bin` or `~/.local/bin` if it exists).

I personally use the following command, inspired from the *haskell-papers-ereader* repository:

`k2pdfopt Build\ Systems\ à\ la\ Carte.pdf -dev kbg -c -om 0.2`

It takes a 1-column paper and generates a PDF suitable for a Kobo Glo, with a a 0.2 inch margin around the document.

You can customize the command for your device using the device profiles listed [here](https://github.com/koreader/libk2pdfopt/blob/master/k2pdfoptlib/devprofile.c#L26), and if you want to process a 2-columns document, append `-mode 2col` to the command line.

[Reading .pdf files comfortably on Kindle](http://blog.refu.co/?p=1158) show even more options, and a way to enable OCR on the file to get a textual PDF as output.
