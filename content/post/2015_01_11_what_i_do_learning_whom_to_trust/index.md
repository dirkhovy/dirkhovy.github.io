---
title: "What I do: Learning whom to trust"
authors: [Dirk Hovy]
date: 2015-01-11
---

Here, I’ll try to explain another paper I have worked on in generally understandable terms. This time, it’s about learning whose opinion we can trust.


Say you are thinking of watching  “Interstellar”. You have seen mixed reviews and want to poll your friends for an opinion. So you ask 6 people. If five say  “don’t bother” and one  “yay”, it’s pretty clear. This is called  “majority voting”.


However, more often than not, you will get a tie, i.e., three people say  “don’t bother” and three  “yay”. This gets worse the more answer options there are: imagine asking six people whether to see  “Interstellar”,  “The Hobbit”,  “Fury”, or  “Unbroken”.


One way to break ties is by flipping a coin (or rolling a die, if you have more than two answer options). However, this has a 50% or higher chance of picking the wrong answer. 


If you knew, however, that one of your friends simply likes all movies and always says yes, and another one has the same taste as you and said no, you would be able to weigh their answers differently. Instead of flipping a coin to break ties, you’d use a weighted average to get the best answer.


In Natural Language Processing, we often ask people for their opinion. Usually, it’s about the part of speech (noun, verb, adjective, etc) of words, or whether a sentence is positive, negative, or neutral. This is called annotation. The annotated text is then used to train statistical models. If the annotation is wrong, the models won’t work as well.


We assume that most annotators are generally trustworthy, but that some annotators get it wrong. Either because they did not pay attention to the explanation, or because they don’t care about the task and just want to get paid. If we could down-weigh bad annotators, we would get better annotations and thus better statistical models.


Unfortunately, we usually don’t know the annotators, and thus we don’t know how much to weigh each annotator’s answer. If we did, we could just compute a weighted average over the annotators and get the most likely correct answer. 

If we already knew the correct answers, we could count how often each annotator gave the correct answer, and use that fraction as weight. 

But we don’t know the correct answer, and we don’t know the weights, so we are stuck in a circular problem.


The way to address this circular problem is by using an algorithm called Expectation Maximization (EM). It works in two steps that are repeated until we reach a satisfying answer. 

Initially, we give each annotator some random weight. In the first step, we then calculate the most likely answers based on the weights. Now we can compute how many answers each annotator got right, and assign them a weight based on that fraction. This is the second step. 

With the new weights, we re-calculate how many answers each annotator gets right, and again update the weights. And again, and again. At some point, the weights don’t change much any more from round to round, and we are done. We now have weights and can compute the most likely final answers.


We also use an additional technique, called Variational Bayes EM, that essentially tells the model that people either do a good job or they don’t care, but nobody cares a little. This is called a  “prior belief”, or just  “prior”. Technically, this works by adding pseudo-counts, i.e., when computing how many answers each annotator got right and wrong, we add a small number (we used 0.5) to both. The reason why this works is complex, but it essentially relativizes the influence of the counts a bit, unless they are pretty strong. In the end, it prevents the model from giving too low weights to actually good annotators and improves performance. 


Using the final weights for each annotator, we can compute a likelihood for each answer under the model (i.e., given that particular set of weights, how likely is a particular answer). The product of all answer likelihoods gives us a measure for how good the model is. Ideally, we would like to have a model with high likelihood.


Since we started out with random weights, there is a chance that a bad annotator ends up with a high weight. It’s a small chance, because the training process tends to correct that, but it exists. To eliminate that chance, we run the training several times, every time with different starting weights. Once a training run finishes, we measure the overall likelihood of the model. We then pick the final set of weights that resulted in the highest overall likelihood.


We implemented all this in a model and called it MACE, which stands for Multi-Annotator Competence Estimation, because a) that describes what it does and b) we thought it sounded funny to say  “Learning whom to trust with MACE” (yes, this is how scientists work).


When we tested MACE on data sets where we already knew the correct answer, we found that MACE correctly finds more than 90% of the answers, while majority voting (with coin flipping to break ties) does much worse.


In real life, we of course don’t know the correct answers, but we found in several annotation projects that the MACE answers produce better statistical NLP models than when using majority voting annotations. We also found that annotators who get a low weight usually also produce bad work, while the ones with high weights produce good annotations.


Since we have probabilities for each answer, we can also choose to focus on the ones with high probabilities. If we do that, we see that the accuracy for those answers is even higher than for all. This is interesting for the case where we have some more annotations than we need, but would like to know that the ones we choose are of especially high quality.


When asking people to annotate, we can also smuggle test questions in there where we know the correct answer. These are called control items (because we can control how good the annotators are). That way, we can sort out bad apples even more accurately. If we use even just a few control items in MACE, accuracy goes up even further.


When I gave a talk about MACE, one of the listeners asked what would happen if my annotators were a bunch of monkeys: would MACE still find the  “experts”? The answer is no, but it’s a good question, and we actually did test how many  “good” annotators the model needs to find good answers. We simulated 10 annotators and varied the number of good ones: those would get 95% of the answers correct (this is roughly the percentage of the best annotators in real life). The rest of the simulated annotators would pick an answer at random or always choose the same value. We found that even with just 3 or four good annotators, MACE was much better in recovering the correct answer than majority voting. Luckily, in real life, it is pretty unlikely to have such a bad crowd of annotators. Just don’t use monkeys.


Whether we have control items or not, we can use MACE to get better answers for our annotation projects, and learn in the process which annotators are doing a good job. 


The paper I explained here is this one, and MACE can be downloaded here.
