.. post:: August 10, 2020
   :tags: self-supervised learning, data augmentation
   :category: Lit

Trevor Darrell's Self Supervision Papers
========================================

Due to the ensembling results I was getting, John recommended that I take a look at Trevor Darrell's recent work with self supervised learning. Here I'm going to describe two papers by his group (:cite:p:`Reed.2020,Reed.2021`) that apply self supervision to the task of representation learning- learning good representations that you can use to initialize networks for a variety of downstream tasks. In general, lots of work in self supervision is then evaluated by sticking on a linear layer at the top, which gets trained for certain downstream tasks (sometimes the main network is fine tuned, sometimes not). In general though, these self supervision papers assume the goal of self supervision is good representation learning for downstream tasks, which is a little different from what I'm doing.  

SelfAugment: Automatic Augmentation Policies for Self-Supervised Learning (Reed 2020)
-------------------------------------------------------------------------------------

**What is this paper doing?** This paper assumes a current workflow for self supervised learning in which people first find good data augmentations with supervised learning based evaluations, and then use these data augmentations for instance contrastive learning (think comparing positive and negative examples via InfoNCE). This paper has two main results that demonstrate the usefulness of self-supervised training to learn good data representations for downstream supervised learning tasks. First, it shows that there are self-supervised tasks (in particular, identifying image rotations) that correlate well with supervised learning based representations, removing the need for supervised data to evaluate data augmentations. Second, it suggests an adaptation of existing data augmentation search strategies (which are themselves informed by the NAS literature) to this self-supervised setting, thereby establishing a fully self supervised pipeline for generation of good representations. 

**Why is it significant?** This paper removes the need for training data from a self-supervised representation learning pipeline, and shows as a separate interesting result that image rotation may be an interesting task due to the correlation of its learned representations with downstream supervised tasks. 

**How does it relate to your work?** The focus of this paper is on data augmentation as a prerequisite to learning good self-supervised representations, and self-supervised network performance. There are a few interesting ways this could relate to your work:
    1. We use pretrained imagenet networks that are supervised in pretraining. It might be interesting to replace these with self supervised ones (see the next area for more info on this). 
    2. The approach taken here to data augmentation is very sophisticated compared to data augmentation that I'm familiar with. Could you find a good way to engage in smart data augmentation with your approach? 
    3. Self supervision here means using contrastive estimation to learn good representations of the data. How does this relate with how John saw self supervision in your work? You showed that certain frames are actively detrimental to classification performance in a certain regime. Somehow, they detract from the generalization performance by enforcing spurious correlations in the data. How can ensembles fit into the self supervision framework? Compare them to something about supervised evaluation to come up with a data augmentation strategy. Maybe there's something about frames that cause disagreement that you want to consider (or stand out) in a self-supervised task. **What if we did self supervision to create a relational representation of the data?** Not just about contrasting with other data points, but also establishing the right kinds of similarity. Self supervised clustering?    

Self-Supervised Pretraining improves Self-Supervised Pretraining (Reed 2021)
----------------------------------------------------------------------------

This paper goes more into the 


.. bibliography:: 
