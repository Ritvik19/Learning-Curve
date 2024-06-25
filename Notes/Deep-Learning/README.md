# Deep Learning

You can think of a deep network as a multistage information- distillation process, where information goes through successive filters and comes out increasingly purified (that is, useful with regard to some task).

In deep learning, everything is a vector—that is to say, everything is a point in a geometric space. Model inputs (text, images, and so on) and targets are first vectorized turned into an initial input vector space and target vector space. Each layer in a deep learning model operates one simple geometric transformation on the data that goes

through it. Together, the chain of layers in the model forms one complex geometric transformation, broken down into a series of simple ones. This complex transformation attempts to map the input space to the target space, one point at a time. This transformation is parameterized by the weights of the layers, which are iteratively updated based on how well the model is currently performing.

That’s the magic of deep learning: turning meaning into vectors, then into geometric spaces, and then incrementally learning complex geometric transformations that map one space to another. All you need are spaces of sufficiently high dimensionality in order to capture the full scope of the relationships found in the original data.

The whole process hinges on a single core idea: that meaning is derived from the pairwise relationship between things (between words in a language, between pixels in an image, and so on) and that these relationships can be captured by a distance function.

In particular, neural networks have hardly anything to do with the brain. A more appropriate name would have been **layered representations learning** or **hierarchical representations learning**, or maybe even **deep differentiable models** or **chained geometric transforms**, to emphasize the fact that continuous geometric space manipulation is at their core.