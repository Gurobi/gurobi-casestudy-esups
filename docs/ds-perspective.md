# A Data Scientist's Perspective

As you begin to approach this problem, your first instinct might be to leverage machine learning (ML) tools. After all, the problem appears well-suited for machine learning: We have an implicit reward function in how well our allocation meets the demand for supplies, perhaps discounted by transit time and cost.  We also have defined inputs (amount of supply and available warehouses) and outputs (where to store the supplies).

But just because the inputs and outputs are clear, doesn’t mean the program is easy to implement. Let’s look at what solving this with ML tools would look like in practice.

## A Machine Learning Approach

When considering (ML) approaches for complex problems, **neural networks (NNs)** are often one of the first tools that come to mind. This is understandable, as NNs are powerful function approximators capable of learning intricate patterns and relationships from large datasets. Given enough data and model capacity, they can approximate any function to arbitrary precision (a property known as the Universal Approximation Theorem).

However, for this case study on disaster relief in Madagascar, we face significant constraints. We have reliable data on only **64 disaster events**, with each event characterized by limited features—primarily location, type, and impact. Additionally, our objective involves optimizing **supply allocations** for **13 different items** across **27 warehouses**. The challenge here is substantial: we must map a small, sparse dataset with limited features to a vast solution space, all while contending with a noisy reward function that makes it difficult to gauge success. 


## Challenges with Sparse Data and Neural Networks

Sparse data is a notorious problem in machine learning. With only 64 data points, a neural network would struggle to generalize well, especially given the high-dimensional output space—13 items across 27 warehouses—resulting in 351 decision variables. 

Now, there are several ways to deal with sparse data in ML, and you might have your own technique you want to try—and you absolutely should! If you find interesting results, we’d love to hear about them. But for now, let’s consider one of the most popular techniques: data interpolation.

**Data interpolation** attempts to create a probability distribution that closely mirrors real-world events, allowing us to sample synthetic data for training. Ideally, this synthetic data is representative enough that a neural network can learn from it. However, generating such a distribution is often as challenging as the original problem—especially when the relationships are highly complex or unpredictable. For instance, allocating goods based on past data might work, but predicting the location, type, and impact of future disasters introduces an additional layer of complexity.

Likely the first method that comes to mind when choosing an ML approach is neural networks, and for good reason. Neural networks are incredibly powerful tools that have transformed the modern world— they’re able to approximate any function to arbitrary precision, provided they are large enough and have enough data. However, in this case study, we’ll be drilling down on disasters in Madagascar, for which we only have reliable data on 64 events. To make matters even more complicated, each disaster is characterized by limited information—mainly location, type, and impact.