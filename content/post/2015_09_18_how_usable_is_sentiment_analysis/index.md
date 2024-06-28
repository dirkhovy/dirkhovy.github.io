---
title: "How usable is sentiment analysis?"
authors: [Dirk Hovy]
date: 2015-09-18
---

Recently, I was interviewed by two students for a study on the business application of natural language processing technique called sentiment analysis. Sentiment analysis takes as input a text (which can be anything from a sentence, a tweet, or a paragraph, up to an entire document), and tries to predict the general attitude expressed therein: usually divided into positive, negative, or neutral.


For many businesses, this is an appealing application, since it promises to detect how people think about the company’s products and services, and because it can potentially be used to evaluate stock options.

However, potential and reality differ, and as far as I see it, there are currently three problems that limit the general applicability of sentiment analysis, and their commercial use:


1. The labels:

The labels are fairly coarse (positive, negative, neutral), while there is still an ongoing debate in psychology on how many basic emotions there are (see here). More fine-grained labels (Facebook let’s you label your status with more than 100  “emotions”) might provide better leverage, but the question is: what would they be? Another problem is the relation between text and labels: we recently had a paper accepted which shows that a common approach to labeling (by using ratings) is not strongly correlated with the text, i.e., models (and humans) can’t guess correctly how many stars somebody gave, only based on the review text. This is largely what we expect of our statistical approaches, though. Which brings us to the second problem:


2. The models

The models are usually trained on a particular domain (say, movie reviews), where they learn that certain features are indicative, say for movies the word ’hilarious’. However, when applied to another domain (say, restaurant reviews), this word does not at all indicate positive sentiment (a  “hilarious” meal might not be what we hope for). 

In technical terms, models overfit the training data. For a negative result on this, see here. Models need to be better regularized, i.e., de-biased from the training data, in order not to put too much faith in spurious features. Which finally brings us to the third problem:


3. The features

The problem of most approaches is the reliance on individual words, rather than on global sentiment and a deeper understanding of the text. Many models still rely on predefined word lists, or dictionaries, but individual words do not do the problem justice. Things like negation, sarcasm, or metaphors can completely distort the sense of a phrase, even though the individual words seem unambiguous. Even seemingly clear positive or negative words can often express both sentiments when seen in context, cf.  “sincere” in  “sincere answer” vs.  “sincere condolences”, or  “cold” in  “cold look” vs.  “cold beer” (see Flekova et al.). This doesn’t even begin to cover the problem that different age and gender groups express positive or negative sentiment very differently, yet that the models treat all text as coming from the same demographics.


In sum, our approaches are currently too simplistic to capture the complexity of entire texts, thus making results brittle. The over-reliance on individual words and the lack of model regularization exacerbate this problem.

This is not to say that sentiment analysis does not work at all, but all of this limits the commercial use of sentiment analysis to fairly clearly denominated domains (see also the assessment of Larson and Watson). 

To improve make sentiment analysis viable for a wider range of contexts, though, we have to start improving all of the three areas above.
