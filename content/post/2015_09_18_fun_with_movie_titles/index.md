---
title: "Fun with Movie Titles"
authors: [Dirk Hovy]
date: 2015-09-18
---

As mentioned before, I sometimes use my academic knowledge of natural language processing for purposes other than research.


A friend recently told me about an entertaining game where you gerundivize words in movie titles (i.e., you add -ing at the end) to completely change the meaning. Some of my PG-13 favorites include  “Jurassic Parking”,  “Ironing Man” and  “2001: Spacing Oddysey” (you can get equally entertaining, yet NSFW result with other titles, but I leave that as an exercise to the reader).


Being the spoilsport I am, I decided that it would be fun to see how much NLP could help me with that. It certainly won’t be able to decide whether an altered title is funny or not (that’s how lame AI still really is), but it would at least help me generate all possible versions.


I downloaded a list of the 1000 best movies ever (at least according to The New York Times) and then took each title, went through it word by word, and checked (against the Brown corpus), whether adding ’-ing’ to the end resulted in an English word. If so, I printed it out.


The only tricky part was to deal with the spelling alterations for gerunds: -e is always removed ( “take” becomes  “tak-ing”), consonants are usually doubled ( “put” becomes  “put-t-ing”, but  “model” becomes  “model-ing”). For the latter case, I actually generate both the duplicated and a non-duplicated version (the rules for the game are not quite clear on what to do here). That’s how I got  “Beverly Hills Coping”, which I think sounds much funnier than  “Beverly Hills Copping”.


I didn’t check for grammaticality of the entire title, which results in nonsense such as  “Alice Doesn’t Living Here Anymore”, while other results are just minor changes in meaning ( “Dial M for Murder” vs.  “Dialing M for Murder”). Some of the results are pretty entertaining, though:  “The Counting of Monte Cristo”,  “Lasting Tango in Paris”,  “Gosford Parking”,  “Gone with the Winding”,  “Lone Staring” (creep!),  “Odd Man Outing”,  “Oliver Twisting”,  “Totaling Recall”, or  “Body Heating”. You can download the script here and play around with it to get the full list, or modify it with your own titles.


And that’s it, I wasted another perfectly good hour using NLP for my personal entertainment.
