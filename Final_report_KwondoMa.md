```
---
Name: Kwondo Ma
Topic: [12]
Title: Why do we learn eigenvalue problem in math class?
----
```

# Eigenvalue Problem

The eigenvalue problem is determination of non-trivial solutions of $$Ax = λx$$ for vector $x$ and scalar value $λ$ [1]. Here, the matrix $A$ has to be a square matrix, vector $x$ can not be a zero vector, and scalar $λ$ has to be a real number. The solution vector $x$ is defined as an eigenvector and the corresponding scalar value $λ$ is defined as an eigenvalue.

Let's look into how to solve this eigenvalue problem. Assume that the matrix $A$ is $n \times n$ matrix. Then, the equation can be written as $(A-λI)x = 0$ where $I$ is represented an identity matrix with a size of $n \times n$. For deriving non-trivial solutions, determinant of $A-λI$ part has to be zero as, $det(A-λI)=0$. As long as we have full knowledge of matrix $A$, this is an equation with one unknown variable $λ$ and the order of this equation $n$. Therefore, we can compute the values of $λ$ from this equation (sometimes some of them are not real numbers and in this case, we dont have eigenvalue-eigenvector pairs).

Once we compute the $n$ number of eigenvalues $λ$, we can derive the corresponding eigenvector $x$ by substituting $λ$ into equation $(A-λI)x = 0$. Here, eigenvector $x$ has $n$ unknown variable and we have $n$ number of equation out of initial equation $(A-λI)x = 0$. Therefore, we can specify each eigenvector $x$ from corresponding eigenvalue $λ$.

In conclusion, equation $Ax = λx$ is solved by computing a determinant of matrix $A-λI$ for eigenvalues first, and then derive the corresponding eigenvectors later.

## What are these (eigenvalue, eigenvector) pairs used for?

Multiplication of matrix $A$ is a linear transformation. These are the examples of $2 \times 2$ matrix. 

$$A = \begin{bmatrix} 3 & 0 \\
0 & 0.5 \end{bmatrix}$$

<!--         [ 3   0  ]             [ -1   0 ]            [  0  1 ]  
    A = [ 0  0.5 ]        B =  [  0  -2 ]        C = [ -1  0 ]   -->

For a case of matrix $A$, base of x-axis is stretched by 3 times and base of y-axis is compressed by half. 

$$B = \begin{bmatrix} -1 & 0 \\
0 & -2 \end{bmatrix}$$

$$C = \begin{bmatrix} 0 & 1 \\
-1 & 0 \end{bmatrix}$$

For other examples, the directions of axes can be flipped (for example matrix $B$) or rotated (for example matrix $C$). Let's think about how eigenvector behave under this linear transformation. The linear transformation of vector $Ax$ is identical with a term of $λx$ which is a scalar multiplication of vector $x$. This represents two things: (1) the direction of eigenvector $x$ is preserved under the linear transformation, and (2) the amount of scalar change due to the linear transformation is represented by $λ$.

## Visualization of eigenvalue problem
Here, $A$ is defined as $2 \times 2$ matrix and the figure shows the linear transformation.

<img src=figure1.png width="400" height="300"> [2]

Then, how do pair of eigenvector and eigenvalue look like? It will be explained based on two characteristics that we discussed earlier. The direction of first eigenvector is on x-axis. See you can see here, the direction of x-axis is not change after the linear transformation but it is only stretched by 3. 


<img src=x_axis_base.png width="390" height="300"> [2]
<img src=figure2.png width="390" height="300"> [2]

Let's find second eigenvector and eigenvalue. 

<img src=2nd_vector.png width="390" height="300"> [2]
<img src=2nd_vector_after.png width="390" height="300"> [2]

As you can see it on figures, the direction of $x = (-1, 1)$ is unchanged after the linear transformation but only stretched by 2. Any vector which is not on the span of $(-1,1)$ or $(1,0)$ will be changed its own direction due to the linear transformation. Therefore, we consider the eigenvectors of this matrix $A$ as new bases at the transformed coordinate system due to its linear transformation and the eigenvalues are considered as scalaring factors for this transformation.



## Practical applications using eigenvalue problem
### 1. Apply singular value decomposition for image compression

When we apply singular value decomposition, we can compute dominant eigenvalues and corresponding eigenvectors. Based on this result, if we throw away small eigenvalues of $AA^T$, we can easily compress the image without lose the major information. The figure shows the quality of pictures by different singular values "k". By doing so, we can reduce large amount of memory overhead on various fields. 

<img src=svd.png> [3]

### 2. Dimensionality reduction using principal component analysis

In modern world, we have planty of information, so the key point is how we can extract the essence from the bulk of information. For the perspective of large dataset, the dimensionality reduction emerges to hot topic. Principal component analysis (PCA) is a technique to reduce a high dimensional data into low dimension while preserving the major information. 

<img src=pca.png width="600" height="600"> [4]

PCA computes the eigenvalues of $A^TA$ and its dominant eigenvalues are utilized for dimensionality reduction. For example, the largest eigenvalues from PCA is represented as the least squared projection on the smallest dimensional hyperplane. Also, the corresponding eigenvectors become new axes for this hyperplane. Therefore, the eigenvalue problem on PCA become critical role on machine learning and data analysis.

# Generalized Eigenvalue Problem

The generalized eigenvalue problem is similar with eigenvalue problem that we discussed eariler but there is another matrix $B$ with $λ$ as  $$Ax = λBx$$ where matrix $A$ and $B$ are both $n \times n$ dimension and $λ$ is a real number. 

This generalized eigenvalue problem can be altered to ordinary eigenvalue problem by matrix decomposition. However, for doing so, it requires certain conditions for matrix $A$ and $B$ and more importantly, this problem is often more difficult to analyze because it is ill-conditioned.

# Reference

[1] Wilkinson, James Hardy. The algebraic eigenvalue problem, volume 662. Oxford Clarendon, 1965.

[2] 3Blue1Brown. (2016a, September 15). Eigenvectors and eigenvalues | Chapter 14, Essence of linear algebra. YouTube. https://www.youtube.com/watch?v=PFDu9oVAE-g

[3] Aishwarya, K. M., Ramesh, R., Sobarad, P. M., & Singh, V. (2016, March). Lossy image compression using SVD coding algorithm. In 2016 International Conference on Wireless Communications, Signal Processing and Networking (WiSPNET) (pp. 1384-1389). IEEE.

[4] Wikipedia contributors. (2016, February 8). File:GaussianScatterPCA.svg - Wikipedia. https://en.wikipedia.org/wiki/File:GaussianScatterPCA.svg
