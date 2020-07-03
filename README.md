# Text-Mercato

### Approach

There are two ways of approaching the problem:-

<b>1.	By finding the Similarity between the images.</b>

We can use the imagehash library. Image hashes tell whether two images look nearly identical. We can find the hashes of the images and can apply the cutoff on which we want to group the identical images. And then moving them into a new folder. But the result was not too good. It was giving an accuracy of approximately 55%. 

```python3
from PIL import Image
import imagehash
hash0 = imagehash.average_hash(Image.open('pics/m-rs19stkt-b-rope-original-imafeeug9ak3rpsp.jpeg')) 
hash1 = imagehash.average_hash(Image.open('pics/m-black-gown-pavitra-original-imafn9dhf4fs94gt.jpeg')) 
cutoff = 18
print("Similarity ----> ", hash0 - hash1)

if hash0 - hash1 <= cutoff:
  print('images are similar')
else:
  print('images are not similar')
```

<b>2. Using the K-Means Algorithm</b>

We can cluster the similar image together using the K-Means Algorithm. The algorithm works on generating clusters. The user enters the cluster size and depending on that the algorithm finds the Euclidean distance between the point and the cluster’s centers and then point is grouped into that cluster which has the minimum distance with it. 

In the grouping the images, first we have entered the number of clusters and then we are converting all the images into pixels and then finding their minimum Euclidean distance and grouping those images together and copying those images into the new directory. As the grouping is done based on pixels and distance, the result is not 100% accurate but it is quite good from the 1st approach. 

![picture alt](/Screenshots/K_Means_Clustering.png "K-Means Clustering")

### Result from K-Means Clustering

<b> Product 1 </b>

<img src="/Screenshots/After_Clustering___Product_1.png" height="60%" width="60%">.

<b> Product 2 </b>

<img src="/Screenshots/After_Clustering___Product_2.png" height="60%" width="60%">.

<b> Product 3 </b>

<img src="/Screenshots/After_Clustering___Product_3.png" height="60%" width="60%">.

<b> Product 4 </b>

<img src="/Screenshots/After_Clustering___Product_4.png" height="60%" width="60%">.


<b> Product 5 </b>

<img src="/Screenshots/After_Clustering___Product_5.png" height="60%" width="60%">.


<b> Product 6 </b>

<img src="/Screenshots/After_Clustering___Product_6.png" height="60%" width="60%">.

The result is not 100% accurate but it is much better than 1st approach.

### How to run

- Clone the Repository
- Open Command Prompt
- Change the path to the clone repository
- Run ---> python Distinct_Product.py -f C:\Users\[your_cd_name]\Desktop\pics -k 6 -r 32

Where -k is number of Clusters and -r is resampling the images.
