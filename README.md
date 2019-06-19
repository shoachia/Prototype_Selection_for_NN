# Prototype selection for nearest neighbor
---
### 1. MNIST dataset download
http://yann.lecun.com/exdb/mnist/
### 2. Read MNIST datase as array
```python=
from mnist import MNIST
mndata = MNIST('./mnist')
train_images, train_labels = mndata.load_training()
test_images, test_labels = mndata.load_testing()
train_images = np.array(train_images)
train_labels = np.array(train_labels)
test_images = np.array(test_images) 
test_labels = np.array(test_labels)
```

### 3. Algorithm Description

In this program, an improved selection of training data is proposed. Since random selection in MNIST dataset can get a bad performance in training, we proposed an algorithm to choose the data that are more representative. 

Firstly, use k-means to divide each label into several clusters. This is been performed under the assumption of that all of the American wirte "1" as a perfectly horizontal line and all of Chinese write "1" as a perfectly vertical line. By applying thr k-means algorithm, it can be automatically devide into two different clusters. 

Secondly, we can choose the data points that can better represent each clusters which is simply the data points that are closer the the mean of cluster.

This algorithm successfully improved the results when using a little data points. However, as the training size is able to be large. This algorithm cannot have significant performance.
