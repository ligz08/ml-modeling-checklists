# Dimension Reduction
- Feature *selection* / *engineering* -- you need some domain knowledge
- Feature *extraction* -- more of mathematical manipulation

## Random Projection  
Random projection works on the basis of *Johnson-Lindenstrauss lemma*, 
which states that you can use a random ![](https://latex.codecogs.com/gif.latex?m%20%5Ctimes%20k) matrix to project ![](https://latex.codecogs.com/gif.latex?m) features to ![](https://latex.codecogs.com/gif.latex?k) features, 
while the pairwise distance between your vectors are within error of ![](https://latex.codecogs.com/gif.latex?%5Cepsilon), as long as  
<center><img src="https://latex.codecogs.com/gif.latex?k&space;>&space;\frac{9&space;\ln&space;n}{\epsilon^2&space;-&space;\epsilon^3}" title="k > \frac{9 \ln n}{\epsilon^2 - \epsilon^3}" /> </center>  

Here ![](https://latex.codecogs.com/gif.latex?n) is your sample size, and ![](https://latex.codecogs.com/gif.latex?%5Cepsilon) is the level of error you are willing to accept. 
Obviously, the bigger your sample size (thus more error terms to consider), and the smaller error you can tolerate, 
the larger ![](https://latex.codecogs.com/gif.latex?k) you end up with.

`sklearn` offers a convenient function to find this ![](https://latex.codecogs.com/gif.latex?k), given ![](https://latex.codecogs.com/gif.latex?n) and ![](https://latex.codecogs.com/gif.latex?%5Cepsilon):  
[`sklearn.random_projection.johnson_lindenstrauss_min_dim(n_samples, eps=0.1)`](http://scikit-learn.org/stable/modules/generated/sklearn.random_projection.johnson_lindenstrauss_min_dim.html#sklearn.random_projection.johnson_lindenstrauss_min_dim)

More about random projection at: [Sci-Kit Learn random projection documentation](http://scikit-learn.org/stable/modules/random_projection.html).

### Gaussian Random Projection
`sklearn.random_projection.GaussianRandomProjection()`

### Sparse Random Projection  
`sklearn.random_projection.SparseRandomProjection()`: faster, takes less memory than Gaussian random projection.

### Quality of Random Projection
Use `sklearn.metrics.pairwise_distances()`


## Principle Component Analysis - PCA

### PCA Theory
The objective of PCA is to find several *orthogonal* dimensions to project the data on, 
while preserving the greatest *variance* in data.  

![PCA](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/GaussianScatterPCA.svg/720px-GaussianScatterPCA.svg.png)

In practice, `sklearn` employs the singular vector decomposition (SVD) method to find principal components.

### SVD Theory
Every matrix, square or not, can be decomposed to the product of 3 matrices:  

![SVD](http://images.slideplayer.com/16/5189063/slides/slide_6.jpg)

<center>
<img src="https://latex.codecogs.com/gif.latex?A_{[m&space;\times&space;n]}&space;=&space;U_{[m&space;\times&space;r]}&space;\Sigma_{[r&space;\times&space;r]]}&space;(V_{[n&space;\times&space;r]})^T" title="A_{[m \times n]} = U_{[m \times r]} \Sigma_{[r \times r]]} (V_{[n \times r]})^T" />
</center>

where  
![U](https://latex.codecogs.com/gif.latex?U) is an orthogonal matrix (rotate), the columns if it are *left singular vectors*    
![Sigma](https://latex.codecogs.com/gif.latex?\Sigma): diagonal matrix (stretch), the diagonal values are called *singular values*, they represent "strength" of each dimension  
![VT](https://latex.codecogs.com/gif.latex?V^T): orthogonal matrix  (rotate), the rows are *right singular vectors*  
![r](https://latex.codecogs.com/gif.latex?r): rank of ![A](https://latex.codecogs.com/gif.latex?A), i.e. dimension of "useful information"

What's awesome about SVD is that it extracts useful information from ![A](https://latex.codecogs.com/gif.latex?A).  
Think of ![A](https://latex.codecogs.com/gif.latex?A)'s rows as observations, and columns as features.  
![r](https://latex.codecogs.com/gif.latex?r), 
the rank if ![A](https://latex.codecogs.com/gif.latex?A), is the number of useful "concepts" in ![A](https://latex.codecogs.com/gif.latex?A).  
The singular values in ![Sigma](https://latex.codecogs.com/gif.latex?\Sigma) represent the strengths of each concept represented in ![A](https://latex.codecogs.com/gif.latex?A),  
Values in ![U](https://latex.codecogs.com/gif.latex?U) represent how strongly each *observation* is associated to each concept.  
Values in ![V](https://latex.codecogs.com/gif.latex?V) represent how strongly each *feature* is associated to each concept.

### PCA in Practice   
`sklearn.decomposition.PCA()`  

`sklearn.decomposition.SparsePCA()`


## Manifold Learning
MDS = multi-dimensional scaling