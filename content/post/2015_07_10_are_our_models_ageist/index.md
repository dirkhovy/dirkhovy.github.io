---
title: "Are our models ageist?"
authors: [Dirk Hovy]
date: 2015-07-10
---

A number of comedies hinge on the premise of a young and an old person switching bodies. When a 45-year-old business woman says  “’sup dudes?”, we find this funny (at least some of us), because it goes against our expectations of how people speak. We do have fairly clear ideas of how 45-year-old business women speak, and how teenage guys do, and that these two ways are not the same. To us, this is such a common and intuitive fact about language that breaking it intentionally can have comedic value.


For the models we use in natural language processing (NLP), however, this fact is not at all clear. To them, all language is the same, because we have not taught them about the difference. When I say  “taught”, I don’t mean that we sat them down and explained how language works, of course. We train a model by presenting it with a bunch of input sentences, and with the correct output analyses we expect for them. If the machine has seen enough of these input and output pairs, it can learn a function that maps from an input sentence to the output analysis.


The problem is that almost all of these training pairs came from newspaper articles from the 80s. And that most of these articles were produced by (and for) a specific demographic, which is, broadly speaking, old, white, and male.


We would expect 60-year-old men to have difficulties understanding  “the kids these days”, and so it’s no surprise that our models have exactly the same difficulties. When we give them input sentences from today’s teenagers (e.g., Twitter), they produce incorrect analyses. Of course, tweets are written very differently from newspaper articles, and so for a while now, the field has investigated the influence of the genre on performance. However, genre is not the whole picture: if we feed the models sentences from older people, they do a lot better than on sentences from younger people, even when the genre is the same for both groups.


Again, this is not too surprising, since language changes with every generation. What is surprising, however, is the depth and magnitude of this change. Younger people do not just use different words than older people. If it was that simple, we could just have the machine learn a number of new words. It turns out, however, that the differences go deeper: younger people even put their words together in ways very different from older people.


In order to test this, we ignored the actual words and looked instead at pairs of the words’ parts of speech (noun, verb, adjective, etc.) So  “Dan cooks”  “Mary writes” or  “Frank measures” all become  “NOUN VERB”. We found that in both German and English, the pairs from the older group were much more similar to the training data than the pairs of the younger group were. In other words: younger people use word combinations that are unlike anything our models have seen before. Older people don’t. Consequently, our models are much better at predicting part of speech sequences for the older group. We tested this for both German and English, with the same results.

Pairs of parts of speech are one thing, but linguistically speaking, they are still a fairly shallow phenomenon. 


We also looked at the deep syntactic structure of grammatical functions (subject, verb, object, etc.), where words do not have to be adjacent, but can be on opposite ends of the sentence.

These analysis were interesting in two ways: from a linguistic perspective, and from an NLP perspective. 


Linguists have suspected for a long time that syntax changes with age. However, since syntax is very complex, this was hard to prove: we can put words together in a great number of ways, and you have to observe lots and lots of examples to see even the most common ones. Even then, it is hard to pin down the exact differences, if you don’t know what constructions you are looking for. We got around both problems by analyzing millions of sentences from people whose age we know. Among those, we selected only the most frequent syntactic constructions and compared them. That way, we did not have to specify beforehand which constructions to look for. The pattern analyses was of course less than perfect (remember, our models are biased), but by analyzing large enough numbers and by focusing on frequent constructions, we were able to get enough reliable observations to find significant differences. We expect the differences to be even more pronounced if the analyses were better.


The result of all this is that even the word-order (syntax) of young people is radically different from the older group. So different, in fact, that seeing a certain construction can give the machine a good clue as to how old the person is. Just as it would us humans.

This does of course not mean that one group uses a syntactic construction and the other group doesn’t. It just means that one group uses a construction statistically significantly more often than the other group. 


And the differences don’t just extend to age: we found similar differences again between men and women. What’s even more startling is the fact that these patterns occur in up to 12 different indo-european languages.


The other way in which these findings were interesting, namely for NLP, was that it showed that our models do pick up on demographic differences, albeit in a bad way. There is, however, nothing inherently ageist to the model algorithms: they are not consciously aware of these differences. They simply transform input sentences into output analyses. However, due to their training, they pick up on the language characteristics of the training data. And when the models get new inputs, they expect the language to be the same as before. This shows how brittle our models are, and how susceptible to the language characteristics (the bias) in the training data.


In fact, we found that our models not only did consistently worse on data from young people (in both German and English), but that they also performed worse and worse the more markers of African-American vernacular English (AAVE) were in a text. (They did not, however, perform worse on different genders―at least.)


So you got a bunch of bad analyses, you could say―so what! 


Indeed, if it was just for academic purposes, this would be annoying, but on the whole inconsequential. However, NLP models are increasingly used as go-to tools for unstructured data analysis, both in business and political analysis. If all of these models expect language to come from old white men, and then perform poorly on texts from other demographic groups, we risk systematically ignoring or, even worse, disadvantaging these groups.


Luckily, there are ways to prevent this problem. For one, we can simply train our models on data from more and more demographic groups. In a recent paper, I showed that if we encode age and gender in the models, we get better performance, even under very controlled settings. This means that there is enough signal in the language of different demographic groups that our models can learn to differentiate, and to produce better analyses on a variety of tasks and languages.


This requires, though, that we have enough samples from all demographic groups, and their correct analyses. Both assumptions are unrealistic (for now), because collecting the data and producing the correct analyses takes a lot of time and effort. What’s more, there are dozens of demographic variables: age, gender, education, ethnicity, class, income, etc., and we are only starting to see which ones impact our models. 


If we want to address the problem in earnest, we can’t afford to encode each of these variables explicitly. However, we can also just tell our models to expect demographic differences, and figure out the rest themselves.


In the future, we need to find ways to automatically detect all kinds of variations, and to reduce the impact of them on training our models. We need to teach our models that language varies along demographic lines, but that all of these variations are valid. 


Not only will we improve the quality of our models, we will also produce fairer analyses that benefit everyone the same.

The papers I described can be found here, here, here, and here.
