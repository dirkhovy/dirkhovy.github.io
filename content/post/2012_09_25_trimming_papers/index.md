---
title: "Trimming Papers"
authors: [Dirk Hovy]
date: 2012-09-25
---

Writing your papers in LaTeX is great and you should definitely do it. It makes everything better (with the possible exception of  grammar), but you have to trust it with the formatting. This is where it gets tricky. Most papers have a page limit, and while LaTex makes sure everything lines up perfectly, it does not care about how many pages it takes. Trimming the paper to a certain page limit thus becomes a familiar headache before every deadline. Luckily, you don’t have to rewrite the whole paper to make the limit. Here are some simple tricks I found helpful to save a lot of space.


Don Metzler showed me a great and easy technique to trim your paper considerably:

- find all paragraphs that have three or fewer words on the last line

- shorten those paragraphs so that the last words advance into the previous line

You can leave paragraphs with more than three words on the last line alone, so instead of rewriting everything a bit, you can focus on a few paragraphs.

This only eliminates one line per paragraph, but due to the way LaTex spaces out paragraphs over the page, this actually shortens the overall paper quite a bit. Treat three or four paragraphs that way and you might cut your paper by half a page.


So, how do you shorten those paragraphs? A good way is to get rid of redundant or  “empty” expressions. One that I found myself using way too often is  “especially in the case of”, as in  “This is annoying, especially in the case of long paragraphs”. The expression is perfectly grammatical, but we can convey the same meaning by just using  “especially for”, as in  “This is annoying, especially for long paragraphs”.  “Especially” already singles out a special case, so we don’t have to say it again. We don’t lose any information, but save three words, and―what’s more important in LaTeX―three white spaces. LaTex spaces out words evenly across each line, mainly by varying the size of spaces (it also varies character spacing, but to a lesser degree). So having fewer characters and white spaces shortens the line, which in turn shortens the paragraph, which in turn shortens the page, which in turn allows you to keep your page limit.


Other phrases that can be shortened: verb plus nominalization, if there is a proper verb for it. I find myself using lots of these constructions. Instead of saying  “we used this for our evaluation”, just make it  “we evaluated this”. 

The Chicago manual of Style also identifies these candidates:

 “due to the fact that” =  “because” 

 “in connection with” =  “of”,  “about”, or  “for” 

 “at this (point in) time” =  “now” 


The best way to save space, however, is to delete useless phrases. Many papers include a paragraph which starts with  “The remainder of this paper is structured as follows:…”. I automatically skip ahead if I see this. In a 8-page paper, you do not need an overview: I can get that by just flipping through. After all, that’s what section titles are for. And do sentences like  “We first introduce the problem in Section 1” or  “Section 5 concludes the paper” really add anything to my understanding? Do they need to tell me that the section titled  “Evaluation” will  “present the evaluation of the experiments”?

Leaving this overview-paragraph out saves a lot of space, and does not take anything away from the content.


Of course it’s good to pay attention to these things while writing, and express yourself as clearly and succinctly as possible. But a few of these cases will creep in anyways. And when it is time to trim the paper, they are a good starting point.

If you have more tips or suggestions, please share! Let’s make meeting page limits in LaTex less scary.
