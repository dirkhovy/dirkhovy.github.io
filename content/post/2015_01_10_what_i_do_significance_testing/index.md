---
title: "What I do: Significance Testing"
authors: [Dirk Hovy]
date: 2015-01-10
---

As much as I love languages, one of the things that frustrated me in linguistics was the seeming arbitrariness of theories. There was no way of knowing which one was better than another. That did not stop people from arguing about exactly that, but there was no way of proving it. 

One of the things that most drew me to natural language processing was the possibility to measure and quantify how good a model (and thereby its underlying linguistic theory) was. I was overjoyed. Unfortunately, nothing is that easy.


It turns out that the closer you look, the more difficulties there are. However, there are also solutions. One of them is significance testing. It’s very powerful, but very easy to misunderstand.


While it is easy to compare two models A and B on the same data set and decide which one is better, this says very little about which model is better in general. Model B might be better on this particular data set, but bad on all others (this is called overfitting). We can get a better picture if we compare the two models on more data sets and average over them. Most likely, however, the difference between two good models will be small. 


So even if we used several data sets, there is still a chance that the difference between A and B is just due to some unaccounted peculiarities, or pure coincidence. This chance gets smaller with more data, but it does not disappear. Can we quantify that chance? This is what significance tests are for.


In general, significance tests estimate the probability that the claim that the difference between the models is not coincidence is false. I.e., how likely am I wrong when I say  “the difference is not due to chance”. This probability is the p-value. A p-value of 0.01 thus means: even though we have shown that the difference between the models is not coincidence, there is a 0.01=1% chance that we were wrong. If our significance test value is lower than this 0.01, then we can say that the difference is  “statistically significant at p=0.01”.


Naturally, the lower the p-value, the better. The important point is that significance is binary: either your result is significant at a certain p-value or it isn’t. This is why this list of descriptions for failed significance tests is rather hilarious.


Ok, great. So does that mean if I see a significant result at a small p-value in a paper, the model is good? Unfortunately, no. Because there are a lot of things that can influence the p-value. Here are some.


The most obvious is the test we use. Some tests only work if your data is normally distributed, i.e., if you plot the data, it looks like a bell shape. This is almost never the case in language. Most data looks like a Zipf curve, i.e., it has a steep decline and then a long tail. Any test that makes the normal-distribution assumption is thus bound to give a wrong result.


A good significance test to compare two models is bootstrap sampling: pick a random sample from the data (instances can be repeated) and compare the two models on that. Do this 10.000 times or so. Count how often B is better than A and divide that by 10.000. That’s your p-value. If the result is small, A is probably a better model.

It does not matter how your data is distributed, this gives us a good estimate.


Ok, so are we done now that we have a good test? Again, no. There are more factors, and even if we pick a certain p-value threshold and report significance, we could be wrong.


Say my models analyze sentences. Maybe I need to restrict my analyses to short sentences (say, less than 20 words) for computational reasons. If A does better than B on this sample, I still have no idea whether it will also be better on longer sentences. My significant result is thus only valid for sentences shorter than 20 words. Unless I say this explicitly, my significant result is misleading. If I wanted to deceive people into thinking my model is great, I could look at different lengths and choose to just report the one that gives me a significant result.


Another issue is the measure I use to compare the models. When analyzing the performance of two models on sentences, I can look at how many sentences each gets right, or at how many words. Or I can just look at verbs. Or rather than the correct items, I can look at the error rate of a certain category. Or a whole number of other measures. All of these can be interesting, but if I get a significant result for one measure, it does not mean I get a significant result for all the others. If I was an unscrupulous researcher, I could test all measure and then just report the ones that look best.


Typically, the larger the data and the bigger the difference, the easier to get a low p-value. Somewhat counterintuitively, this does not mean that increasing the sample size will give a significant result. Maybe I just add more examples where A and B are the same, or more where the weaker model is stronger, and so the differences wash out. 


Ultimately, all that a positive significance test can tell us is that the difference between models for this particular data set, under the given conditions, for the given measure is significant at a certain level. That’s a lot of qualifications. 

The best we can do under these circumstances is to use several data sets, several measures, a clear description of what conditions we used, and an appropriate significance test with a low p-value.


That way, when we say A is significantly better than B, we can be more sure that others will be able to replicate that. It’s not much. But it’s much better than guessing.


The paper I am talking about here is this one. If you got interested, please see the references for a number of other good papers on the subject.
