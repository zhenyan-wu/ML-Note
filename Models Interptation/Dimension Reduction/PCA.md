## PCA

### Pre-knowledges
To begin with, let's review the concept of matrix multiplication. Performing a matrix on a vector can be interpreted as a stretched and shrinkaged behaviour. The shape of a unit sphere will be pressed and reshaped to another sphere after multipled by a matrix. 

Different matrixs have different effects. Specially, for a symmetric matrix the effects can be drawn and analyzed seperately, which is the eigenvectors and eigenvalues. The eigenvectors describe the streched direction of a symmetric matrix and the coresponding eigenvalues are the shrinkaged magnitudes. Further, the symmetric property also ensure the orthogonal property among eigenvector with distinct eigenvalue, which provides a great benefit for decomposition. (think of it!!) Once the symmetric property is breaked, the eigenvectors may be neither real nor linearly independent nor orthogonal. (See more in SVD, singular value is the square root of an eigenvalue)

In a word, symmetric matrix has n real eigenvalues and n linear independent and orthogonal eigenvectors which can form a basis for the n-element vectors that it can transform (in R^n space). 

### Input and Output









