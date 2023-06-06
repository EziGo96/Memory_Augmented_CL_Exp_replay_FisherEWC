# Memory_Augmented_CL_Exp_replay_FisherEWC
implementation of experience replay augmented continual learning for 2 classification tasks

**run**-MemAugCL_exp_repl_EWC.ipynb for demo


**Brief analysis of the model's performance and future improvements**

**Task2 (identifying classes 2 & 3):** 
the model performs similarly with experience replay to what it does without any memory augmentation during continiual learning

**Task1 (identifying classes 0 & 1):** 
the performance of the model has slightly degraded as compared to its original performance (accuracy dropped from 93% to 81% due to driop in recall for each class) but the model retains most of its previous knowledge from Task 1 and also performs well on Task 2. Only 20% of the data from Task1 was used for creating the replay buffer.

**Future Improvements**

1. For a sequence of n tasks the memory constraints for storing 20% of all previous data is a concern. Consequently we can use saliency augmented memory compkletion to store only the important features of the previous data and thus reduce memory footprint of replay buffers

2. In case data from previous tasks is not available we can use Elastic weight consolidation regularisation which I have implemented below but its is extremely computationally expensive for large models and large datasets.

3. Alternately we can use knowledge distilaation from different layers from the old model to train the new model while also training it on the new dataset
