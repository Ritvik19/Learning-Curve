# How to Fine Tune

The steps for fine-tuning a network are as follows:

1.  Add our custom network on top of an already trained base network.
2.  Freeze the base network.
3.  Train the part we added.
4.  Unfreeze some layers in the base network. (Note that you should not unfreeze “batch normalization” layers, Otherwise they will keep updating their internal mean and variance, which can interfere with the very small updates applied to the surrounding Conv2D layers.)
5.  Jointly train both these layers and the part we added.