---
coverY: 0
---

# What is Deep Learning

Deep learning is a very popular concept recently. Such a concept is always hyped up by the media, but in fact deep learning or big data or blockchain or internet of things is something that already exists but has been newly packaged in the 21st century.

In the models we mentioned before, similar to SVM or random forest or Bayesian or Gaussian maximum likelihood Bayesian, the parameters in a model are generally less than 1000, but deep learning generally starts from 1000000 parameters.

This requires a lot of computation to update these million parameters, and also requires a good algorithm, otherwise it is very likely that it will not converge.

The 21st century solved both of these problems, especially after 2012, when large-scale graphics cards made large-scale computing possible.

![Gradient Descent Algorithm](../.gitbook/assets/saddle\_point\_evaluation\_optimizers.gif)

The above is the gradient descent algorithm. This algorithm runs on the graphics card and calculates thousands of parameters at the same time until more than 1 million parameters are all updated.



Deep learning requires such a large amount of computation, so what is the benefit?

First of all, deep learning can perform multi-core computing, but algorithms such as SVM are not easy to perform multi-core computing, so many super-large data can be computed using deep learning, but using SVM will get stuck.

Second, deep learning can have better accuracy.

![ILSVRC challenge](<../.gitbook/assets/image (18).png>)

ILSVRC is an image classification challenge. Pursue the lowest error rate and the best accuracy rate. There are a total of 1000 different categories of pictures. The model needs to use the training set to train the labeled pictures and predict the pictures of the validation set.

ILSVRC is a subset of imagenet. The entire ILSVRC dataset is over 100GB in size and requires registration to download (not commercially available). When registering, you can only use the edu mailbox to obtain the data of the original image dataset.

![imagenet](<../.gitbook/assets/image (19).png>)

AlexNet in 2012 was ILSVRC's first winning deep learning network, trained on two graphics cards, and deep learning has created one accuracy miracle after another.

Last but not least, deep learning requires a lot of computation during the training phase, but once the model is trained, the validation phase will require much less computation.

In addition to that, between 2012 and 2016 people have been going after bigger models, but after 2016 it was found that bigger models don't necessarily give better results, so people started checking at smaller models (of course loss some of the accuracy), but as technology improves, many small computational models now achieve better results than the large models of 2012-2016.









## Statistics

Start time of this page: February 2, 2022

Completion time of this page: February 12, 2022
