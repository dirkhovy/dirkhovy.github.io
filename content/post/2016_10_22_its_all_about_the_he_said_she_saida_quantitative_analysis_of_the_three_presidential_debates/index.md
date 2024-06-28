---
title: "It’s All About the He Said, She Said―A Quantitative Analysis of the Three Presidential Debates"
authors: [Dirk Hovy]
date: 2016-10-22
---

It’s All about the He said, She said―A Quantitative Analysis of the Three Presidential Debates


The question what constitutes an acceptable sentence is a matter of taste, and would elicit very different answers from a moral philosopher, a linguist, and a logician. In natural language processing (NLP), the answer is much simpler (or simplistic), and quantifiable: any sentence that could be generated with some probability from a language model.


As the US presidential debates have drawn to a close, much has been said about acceptable and unacceptable language. While NLP is woefully ill-equipped to make moral decisions on what the candidates said, it is pretty useful to analyze how much was said, and how unusual it is. So I spent an afternoon analyzing the transcripts of the three debates, and quantified the findings.


I downloaded the three transcripts, separated out the answers of the two candidates, split them into sentences, and analyzed them with a language model. Without going into to much technical detail: a language model is a statistical model which has been induced from a large collection of text. To use the model, we give it a sentence and ask  “How likely is it to generate this sentence?” The model then returns a probability between 0 and 1. 0 means that the model would never produce this sentence, and 1 that it always would. In practice, neither of them really occur, but numbers are somewhere in between.


The exact numbers depend on what and how much text you used to train the model, how many words in sequence you look at, and how similar your training data was to the texts you analyze. I used a 5-gram SRILM trained on a corpus of 2,584,929 English review sentences. No, this might not be the best model one could use, and if I used it in an application, I would certainly train on something closer to the debates. However, I used the same model for all three debates and both candidates, so independent of the absolute values we get, we can compare the two politicians quantitatively.


So what do we learn?


First of all, Donald Trump says more (1950 sentences, compared to Clinton’s 1136), but he uses fewer words: the median Trump sentence has 11 words, a Clinton sentence 16. The graph below shows the relative distribution of sentence lengths for each candidate (I accounted for the fact that they uttered different amounts of sentences). 


Because the bars are sometimes a little hard to see in front of each other, I also overlaid them with a smoothed curve (kernel density estimator). The dotted lines show the respective median length in words.

We can see that Trump utters more short sentences (under 15 words), and few longer sentences. Clinton, on the other hand, has a lot more of her sentences in the 15-30 word range.


What about the language model? Let’s first look at the likelihood of the sentences. Some explanation: since the probabilities get very small and hard to distinguish, the likelihood of the sentence is typically given as logarithm of the probability. That makes it a larger, but negative number. The closer the number is to 0, the more likely a sentence is under the model.


We again see some noticeable differences: Trump’s sentences are usually more likely than Clinton’s. This is both an effect of the words the two use, but also of the sentence length (longer sentences become less and less likely), and we have already seen that there are noticeable differences in sentence length.


So let’s normalize each sentence likelihood by the sentence length. That gives us the average log probability per word (note that the x-axis scale is much smaller than before).


Even here, on a per-word-basis, we see that the model is more likely to produce Trump sentences rather than Clinton sentences (you can actually use language models to generate sentences, often to great comical effect, but there isn’t enough training data for each candidate to really come up with much. I tried).


So what do the different sentences look like? Well, the two highest scoring sentences (measured by logprob/word) for each candidate are  “Because I was a senator with a Republican president .” (Clinton) and  “Horribly wounded .” (Trump). The most  “average” sentences are  “But let ’ s not assume that trade is the only challenge we have in the economy .” (Clinton) and  “When we have $ 20 trillion in debt , and our country ’ s a mess , you know , it ’ s one thing to have $ 20 trillion in debt and our roads are good and our bridges are good and everything ’ s in great shape , our airports .” (Trump). Both of these buck the length-trend. The least likely sentences of each candidate, however, do follow what we have seen before:  “Donald thinks belittling women makes him bigger .” (Clinton) vs.  “Trump Foundation , small foundation .” (Trump).


So independent of what the candidates are talking about, the way how they talk can help us separate them to some extent. In fact, if we use only the number of words and logprob as features, we can train a logistic regression classifier that distinguishes the two candidates with an accuracy of over 65% (10-fold cross-validation). That’s only slightly better than the majority class (about 63% accuracy) and again not good enough to build a system, but interesting given that we have not even looked at what the candidates are saying.


Does this tell us anything about the likely outcome in November? No. But it shows that the differences between the candidates’ rhetoric styles go beyond what they say in a quantifiable way: sentence length and predictability.
