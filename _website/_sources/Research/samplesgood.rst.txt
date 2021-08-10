.. post:: August 10, 2020
   :tags: data, ml
   :category: Res
   :author: me
   :location: NYC
   :language: en

Are More Training Samples Always Good? 
======================================

Common knowledge in the machine learning community is that adding more data is always a good idea, and low data methods like n-shot learning (for small n) normally require the introduction of strong inductive biases in order to achieve good performance. However, if we think about the eventual goal of our networks as generalization, does adding more training data really always help? Some recent studies would suggest that the answer is no.  

Pleiss 2020
-----------

First, consider the case of :cite:p:`Pleiss.2020`. This paper introduces a new metric, AUM (area under margin) that keeps track of the relative probability afforded to a given sample's classification output over the course of training. AUM produces a ranking at the end of some training period, with highest ranked samples representing those that are somehow most representative of a given class, and lowest ranked samples representing those that are least representative. Surprisingly, the authors show that by removing low AUM samples based on a given threshold, network performance can be dramatically increased, even outperforming the same networks with data augmentation. While this could be an effect of mislabeled data, there is no way for AUM to distinguish between mislabeled and simply challenging samples, making this an interesting result for further exploration.  

Feldman 2020
------------

Next, consider :cite:p:`Feldman.2020`. This paper does not look at training dynamics, but rather the performance of a family of networks that subsample the full training set. For each training frame, we then ask what the marginal effect of including or excluding that training frame was on performance, somewhat similar to the `Shapley value <https://christophm.github.io/interpretable-ml-book/shapley.html>`_  as it has been used in Machine Learning previously. The paper introduces new efficient estimators to *influence functions* that measure the amount to which a particular training datapoint changes the probability of any test data's groundtruth category being correctly selected. Although their interest is in measuring the distribution of positive influence functions, if we look into their `precomputed influence functions <https://pluskid.github.io/influence-memorization/>`, we see negative influence values, at the very least in CIFAR data, even when only looking at influence between points with the same class assignment. While increasing model uncertainty is definitely a good idea (and in general, most models are overconfident), its unclear if the influence of each data point is strictly positive. 

Nakkiran 2019
-------------

Finally, in a slightly different setting, :cite:p:`Nakkiran.2019` show the existence of "double descent curves" that characterize the change in performance of a family of network models as you increase 1) the number of parameters and 2) the number of training epochs. They show that there is a training-set dependent peak in the cost as you increase both of these parameters in Figure 11b and 15, both for deep networks and for linear models (Random Fourier Features). They hypothesize that this is because models may become more or less sensitive to even small amounts of noise in the training set.   

Ngiam 2018
----------

This paper looks at pretraining: TO READ

Conclusion
----------

All of these examples assume or show that there is some noise in the training labels, whether that noise be misassignments, or simple ambiguity. While some might argue that there is no label noise in large datasets (see citations of :cite:p:`Pleiss.2020,Feldman.2020`) it appears that we'll always have these kinds of ambiguities in our training set. For the case of keypoint detection, this is more true than in many other cases, as target maps might overlap with bad features and create distractors. Understanding the level of ambiguity introduced by a certain training point, and incorporating that ambiguity into the training cost, as considered by other training objectives (:cite:p:`Chapelle.2001,Zhang.2017`) 



.. bibliography:: 

