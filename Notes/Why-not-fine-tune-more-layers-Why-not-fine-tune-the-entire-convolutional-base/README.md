# Why not fine-tune more layers Why not fine-tune the entire convolutional base

You could. But you need to consider the following:

1.  Earlier layers in the convolutional base encode more generic, reusable features, whereas layers higher up encode more specialized features. It’s more useful to fine-tune the more specialized features, because these are the ones that need to be repurposed on your new problem. There would be fast-decreasing returns in fine-tuning lower layers.
2.  The more parameters you’re training, the more you’re at risk of overfitting. The convolutional base has millions of parameters, so it would be risky to attempt to train it on your small dataset.