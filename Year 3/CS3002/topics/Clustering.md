
- There are different classes of learning:
	- Unsupervised learning - learning without the desired output ('teacher' signals)
	- Supervised learning: learning with the desired output
	- Reinforcement learning - reward/punishment signals


## What is clustering

- Clustering: to partition a data set into subsets (clusters), so that the data in each subset share some common trait - often similarity or proximity for some defined distance measure
	- The process of organising objects into groups whose members are similar in some way
	- A **cluster** is therefore a collection of objects which are "similar" between them and are "dissimilar" to the other objects belonging to other clusters
	- It is unsupervised so there is no need for the "teacher" signals (desired output)

- Clustering is one of the widely-used unsupervised learning methods
- Other unsupervised learning methods include:
	- Dimensionality reduction (e.g. PCA)
	- Association Rules / Recommender Systems

- An example of clustering is how a baby is able to differentiate images of cats from dogs and then associate the cats with the dogs

### Patterns, clusters, and features

![](clustergraph.png)

- Clustering is used for a lot of other things too such as:
	- Social networks
	- Customer segmentation
	- Gene networks
	- etc.


## How do you do clustering?

- Given some data x (with 2 features):
![](example.png)

- Pattern similarity:
	- Clusters are formed by similar patterns
	- In computer science, we need to define some metric to measure similarity
	- One of the commonly adopted similarity metrics is **distance**
	- Works on any number of features in a dataset (here $N$):

	$$Euclidean: d(x,y) = \sqrt((x_1 - y_1)^2+(x_2 - y_2)^2 + ...+(x_N - y_N)^2)$$
	$$Manhattan: d(x,y) = |x_1-y_1|+|x_2-y_2|+...+|x_N-y_N|$$
- The shorter the distance, the more similar the two patterns