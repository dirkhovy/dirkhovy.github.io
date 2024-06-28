---
title: "Wow: Such Meme, Much NLP, Very Generate!"
authors: [Dirk Hovy]
date: 2015-09-01
---

I love natural language processing, I really do. I think it has the potential to make the world a little bit better, and like all things worth exploring, it also has the potential to do evil. But it can be tiring wielding all this awesome technology for such serious causes, and sometimes, a man just wants to have a little fun with his subject. After all, why not get a laugh out of all the time invested?


Turns out, you can have a lot of fun with NLP, and it usually only takes a few lines of code and some data. An internet age ago (i.e., last year or so), the Doge meme took the Web by storm, and after seeing it enough, I realized that it followed a certain pattern, and that much of the humor derived from the ungrammatical use of intensifiers with certain word types (I’m a lot of fun at parties, I swear). Essentially, the pattern is

 “Wow, such ADJECTIVE! Much NOUN! Very VERB!” 


All I had to do now was to get all nouns, verbs, and adjectives out of an annotated corpus (I used the Brown corpus, which comes with the NLTK library), and then randomly pick one of each category to fill the slots. Oh, yeah, and I converted all verbs to their infinitive (i.e,. ’jumped’ and ’jumping’ become ’jump’).


The results range from the mundane and stupid to the insightful and funny. My favorites are the jaded look on counter culture in  “Wow, such underground! Much intentions! Very smell!” and the strangely place-appropriate  “Wow, such scandinavian! Much concrete! Very constitute!” 


And that’s it. The entire script is 6 lines of Python code. You can download the script here and play around with it. Enjoy!
