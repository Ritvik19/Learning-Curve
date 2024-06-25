# Why we shouldn't use bias when using BatchNormalization

Because the normalization step will take care of centering the layer’s output on zero, the bias vector is no longer needed when using BatchNormalization, and the layer can be created without it. This makes the layer slightly leaner.