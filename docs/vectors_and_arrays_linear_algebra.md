---

**Foreword**

Code snippets and excerpts from the tutorial. Python 3. From DataCamp.
---

# The Essentials of Numpy: `ndarray`


```python
%pylab inline
import numpy as np

myArray = np.array([[1, 2, 3], [4, 5, 6]], dtype = np.int64)
print(myArray)
```

    Populating the interactive namespace from numpy and matplotlib
    [[1 2 3]
     [4 5 6]]



```python
# Inspect the data of `myArray`
print(myArray.data)
```

    <memory at 0x7f7bbcb71a68>



```python
# Inspect the data type of `myArray`
print(myArray.dtype)
```

    int64



```python
# Inspect the shape of `myArray`
print(myArray.shape)
```

    (2, 3)



```python
# Inspect the size of `myArray`
print(myArray.size)
```

    6


- Convert with `astype()`.
- Handle complex numbers.


```python
# Return the real part of `myArray` elements
np.real(myArray)
```




    array([[1, 2, 3],
           [4, 5, 6]])




```python
# Return the imaginary part of `myArray` elements
np.imag(myArray)
```




    array([[0, 0, 0],
           [0, 0, 0]])




```python
# Return a real array if the complex parts are close to 0
np.real_if_close(myArray,tol=1000)
```




    array([[1, 2, 3],
           [4, 5, 6]])




```python
# Cast `myArray` to float
np.cast['f'](myArray)
```




    array([[ 1.,  2.,  3.],
           [ 4.,  5.,  6.]], dtype=float32)




```python
# Cast `myArray` to integer
np.cast['q'](myArray)
```




    array([[1, 2, 3],
           [4, 5, 6]], dtype=int64)



- `'b'` for int8.
- `'c'` for |S21; character or string.
- `'e'` for float16
- `'f'` for float32.
- `'g'` for float128
- `'h'` for int16, integer.
- `'d'` for digits.
- `'i'` for int32, integer.
- `'l'` for long.
- `'m'` for timedelta64.
- `'q'` for int64, integer.

# Array Creation


```python
# Create a 2X2 identity matrix with `np.eye()`
np.eye(2)
```




    array([[ 1.,  0.],
           [ 0.,  1.]])




```python
np.eye(2, 4)
```




    array([[ 1.,  0.,  0.,  0.],
           [ 0.,  1.,  0.,  0.]])




```python
np.eye(4, 2)
```




    array([[ 1.,  0.],
           [ 0.,  1.],
           [ 0.,  0.],
           [ 0.,  0.]])




```python
# Create a 3X3 identity matrix with `np.identity()`
np.identity(3)
```




    array([[ 1.,  0.,  0.],
           [ 0.,  1.,  0.],
           [ 0.,  0.,  1.]])




```python
# Uniformly spaced values: spacing; from 2 to 8 (excluded) by 2
np.arange(3, 8, 2)
```




    array([3, 5, 7])




```python
# Uniformly spaced values: number of samples; from 2 to 3 in 5 intervals
np.linspace(2, 3, 5)
```




    array([ 2.  ,  2.25,  2.5 ,  2.75,  3.  ])




```python
# Uniformly spaced values: logarithmic spacing; from 2 to 3 in 4 intervals 
np.logspace(2, 3, 4)
```




    array([  100.        ,   215.443469  ,   464.15888336,  1000.        ])



## Indexing and Slicing


```python
print(myArray)
```

    [[1 2 3]
     [4 5 6]]



```python
# Slice `myArray` at index 0 and 1
print(myArray[0,0:2])
```

    [1 2]



```python
# Slice `my_2dArray` at row 0 and 1, column 1
print(myArray[0:2,1])
```

    [2 5]



```python
# Slice `my_3dArray` at row 1
print(myArray[1,...])
```

    [4 5 6]



```python
# Boolean indexing: only values < 3
print(myArray[myArray<3])
```

    [1 2]



```python
# Fancy indexing; r-c coordinates
print(myArray[[1, 0, 1, 0],[0, 1, 2, 0]])
```

    [4 2 6 1]


**Meshgrid**

- Index tricks: `np.mgrid()`, `np.ogrid()`, `np.r` and `np.c`.
- Instead of `np.concatenate()`.
- `np.meshgrid()`.


```python
# Create a dense mesh grid; from to (excluded) by
# takes two 1D arrays and produces two 2D matrices 
# corresponding to all pairs of (x, y) in the two arrays
# the dimensions and number of the output arrays are equal
# to the number of indexing dimensions
np.mgrid[1:11:2, -12:-3:3]
```




    array([[[  1,   1,   1],
            [  3,   3,   3],
            [  5,   5,   5],
            [  7,   7,   7],
            [  9,   9,   9]],
    
           [[-12,  -9,  -6],
            [-12,  -9,  -6],
            [-12,  -9,  -6],
            [-12,  -9,  -6],
            [-12,  -9,  -6]]])




```python
# Create an open meshgrid; from to (excluded) by
np.ogrid[1:11:2, -12:-3:3]
```




    [array([[1],
            [3],
            [5],
            [7],
            [9]]), array([[-12,  -9,  -6]])]




```python
# Stack arrays vertically
np.r_[3, [0]*5, -1:1:10j]
```




    array([ 3.        ,  0.        ,  0.        ,  0.        ,  0.        ,
            0.        , -1.        , -0.77777778, -0.55555556, -0.33333333,
           -0.11111111,  0.11111111,  0.33333333,  0.55555556,  0.77777778,  1.        ])




```python
array = np.ones(2)
my2Array = np.array([[1,2,3,4],[5,6,7,8]])
print(array)
```

    [ 1.  1.]



```python
print(my2Array)
```

    [[1 2 3 4]
     [5 6 7 8]]



```python
# Stack arrays horizontally (left-right)
np.c_[array]
```




    array([[ 1.],
           [ 1.]])




```python
np.c_[my2Array]
```




    array([[1, 2, 3, 4],
           [5, 6, 7, 8]])




```python
np.c_[array, my2Array]
```




    array([[ 1.,  1.,  2.,  3.,  4.],
           [ 1.,  5.,  6.,  7.,  8.]])




```python
array2 = np.array([[1,2,3,4], [1,2,3,4]])
print(array2)
```

    [[1 2 3 4]
     [1 2 3 4]]



```python
np.r_[array2]
```




    array([[1, 2, 3, 4],
           [1, 2, 3, 4]])




```python
np.r_[my2Array]
```




    array([[1, 2, 3, 4],
           [5, 6, 7, 8]])




```python
np.r_[array2, my2Array]
```




    array([[1, 2, 3, 4],
           [1, 2, 3, 4],
           [1, 2, 3, 4],
           [5, 6, 7, 8]])



**Other indexing/slicing**


```python
# Initialize a 2D array 
my_2dArray = np.array([[1,2,3,4], [5,6,7,8]], dtype=np.int64)
print(my_2dArray)
```

    [[1 2 3 4]
     [5 6 7 8]]



```python
# Select values from `my_2dArray`
# argument 1: select
# argument 2: transform
np.select([my_2dArray < 4], [my_2dArray])
```




    array([[1, 2, 3, 0],
           [0, 0, 0, 0]])




```python
np.select([my_2dArray < 4], [my_2dArray * 2])
```




    array([[2, 4, 6, 0],
           [0, 0, 0, 0]])



## Shape Selection and Manipulation

- Stack.
- Split.
- Transpose.
- Change shape.


```python
myArray = np.array([[1, 2, 3, 4]])
my_2dArray = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])
```


```python
print(myArray)
```

    [[1 2 3 4]]



```python
print(my_2dArray)
```

    [[1 2 3 4]
     [5 6 7 8]]



```python
# Stack arrays horizontally (column-wise)
print(np.hstack((np.eye(2), my_2dArray)))
```

    [[ 1.  0.  1.  2.  3.  4.]
     [ 0.  1.  5.  6.  7.  8.]]



```python
# Stack arrays vertically (row-wise)
print(np.vstack((myArray, my_2dArray)))
```

    [[1 2 3 4]
     [1 2 3 4]
     [5 6 7 8]]



```python
# Split the array horizontally at the 2nd index (left-right)
print(np.hsplit(my_2dArray, 2))
```

    [array([[1, 2],
           [5, 6]]), array([[3, 4],
           [7, 8]])]



```python
# Split the array vertically at the 2nd index (top-bottom)
print(np.vsplit(my_2dArray, 2))
```

    [array([[1, 2, 3, 4]]), array([[5, 6, 7, 8]])]



```python
# Permute `myArray` dimensions
print(np.transpose(myArray))
```

    [[1]
     [2]
     [3]
     [4]]



```python
my_3dArray = np.array([[[1, 2, 3, 4], [5, 6, 7,  8]], [[1, 2, 3, 4], [9, 10, 11, 12]]])
print(my_3dArray)
```

    [[[ 1  2  3  4]
      [ 5  6  7  8]]
    
     [[ 1  2  3  4]
      [ 9 10 11 12]]]



```python
# Flatten `my_3dArray`
print(my_3dArray.flatten())
```

    [ 1  2  3  4  5  6  7  8  1  2  3  4  9 10 11 12]


**`np.reshsape()` vs `np.resize()`**.


```python
# Reshape but don't change the data
print(my_2dArray.reshape(4,2))
```

    [[1 2]
     [3 4]
     [5 6]
     [7 8]]



```python
# Resize to (6,4)
print(np.resize(my_3dArray, (6,4)))
```

    [[ 1  2  3  4]
     [ 5  6  7  8]
     [ 1  2  3  4]
     [ 9 10 11 12]
     [ 1  2  3  4]
     [ 5  6  7  8]]


**Vectorized functions (to 'loop' over an array, all items)**


```python
# Define a function `myfunc`
def myfunc(a,b):
  if a > b:
     return a - b
  else:
     return a + b
    
# Vectorize `myfunc`
vectorizedFunc = np.vectorize(myfunc) 

# Apply
print(myArray)
vectorizedFunc(myArray, 2)
```

    [[1 2 3 4]]





    array([[3, 4, 1, 2]])



`np.angle()` provides the angle of the elements of complex array elements, but also basic trigonometric, exponential or logarithmic functions.

# Linear Algebra With Scipy


```python
import scipy

# Check package version
scipy.__version__
```




    '0.19.0'



## Vectors and Matrices: The Basics


```python
# Create a vector
myVector = np.array([1,2,3,4])
print(myVector)
```

    [1 2 3 4]


- A matrix is a subclass of arrays.
- A matrix is always 2D.
- Both arrays and matrices have `.T()`.
- Only matrices have `.H()` and `.I()`.
- Matrix multiplication works differently from an element-wise array.
- T`**` has different results for matrices and arrays.
- Sparse matrices have mostly zero elements, while the ones that have mostly non-zero elements are called dense matrices.
    - `scipy.linalg`.
    - `scipy.sparse`.


```python
# Create a matrix
myMatrix = np.matrix(np.random.random((5,5)))
print(myMatrix)
```

    [[ 0.45409417  0.51518628  0.21891525  0.4827949   0.11485953]
     [ 0.26387125  0.27904581  0.27371679  0.81793744  0.03194194]
     [ 0.44758032  0.40043501  0.53270025  0.73481508  0.40994865]
     [ 0.26650523  0.47469863  0.77731378  0.33237448  0.0932401 ]
     [ 0.47477976  0.4054091   0.62060959  0.76708818  0.33732755]]



```python
# Create a 2X2 identity matrix
np.eye(3, k=1)        
```




    array([[ 0.,  1.,  0.],
           [ 0.,  0.,  1.],
           [ 0.,  0.,  0.]])




```python
# Create a 2x2 identity matrix
np.mat(np.identity(2))         
```




    matrix([[ 1.,  0.],
            [ 0.,  1.]])




```python
C = np.matrix([[0.47332239,0.26149519,0.,0.01665965,0.05914868], [0.24440216,0.,0.,0.,0.],  [0.,0.,0.4320679,0.10501837,0.], [0.32164578,0.,0.,0.10963973,0.],  [0.15023766,0.04764381,0.,0.,0.38244847],  [0.08499095,0.,0.0163261,0.,0.27636168], [0.,0.36569833,0.34968224,0.,0.40275066],  [0.,0.,0.,0.40504002,0.],  [0.41632136,0.35405707,0.33020532,0.16344026,0.], [0.04105013,0.26913226,0.,0.00280266,0.]])
```


```python
print(C)
```

    [[ 0.47332239  0.26149519  0.          0.01665965  0.05914868]
     [ 0.24440216  0.          0.          0.          0.        ]
     [ 0.          0.          0.4320679   0.10501837  0.        ]
     [ 0.32164578  0.          0.          0.10963973  0.        ]
     [ 0.15023766  0.04764381  0.          0.          0.38244847]
     [ 0.08499095  0.          0.0163261   0.          0.27636168]
     [ 0.          0.36569833  0.34968224  0.          0.40275066]
     [ 0.          0.          0.          0.40504002  0.        ]
     [ 0.41632136  0.35405707  0.33020532  0.16344026  0.        ]
     [ 0.04105013  0.26913226  0.          0.00280266  0.        ]]



```python
from scipy import linalg, sparse
```


```python
# Compressed Sparse Row matrix
# fast access to rows and columns
sparse.csr_matrix(C)
```




    <10x5 sparse matrix of type '<class 'numpy.float64'>'
    	with 26 stored elements in Compressed Sparse Row format>




```python
# Compressed Sparse Column matrix
# fast access to  rows and columns
sparse.csc_matrix(C)  
```




    <10x5 sparse matrix of type '<class 'numpy.float64'>'
    	with 26 stored elements in Compressed Sparse Column format>




```python
# Dictionary Of Keys matrix
# fill the matrix with numbers one by one
sparse.dok_matrix(C)  
```




    <10x5 sparse matrix of type '<class 'numpy.float64'>'
    	with 26 stored elements in Dictionary Of Keys format>




```python
# block Sparse Row matrices
# constructing the matrix from blocks of smaller matrices
sparse.bsr_matrix(C)
```




    <10x5 sparse matrix of type '<class 'numpy.float64'>'
    	with 26 stored elements (blocksize = 1x1) in Block Sparse Row format>




```python
# COOrdinate format sparse matrices
# fill the matrix with numbers one by one
sparse.coo_matrix(C)
```




    <10x5 sparse matrix of type '<class 'numpy.float64'>'
    	with 26 stored elements in COOrdinate format>




```python
# DIAgonal storage sparse matrices
# initialize the matrix with an array as the diagonal
sparse.dia_matrix(C)
```




    <10x5 sparse matrix of type '<class 'numpy.float64'>'
    	with 47 stored elements (13 diagonals) in DIAgonal format>




```python
# Row-based linked list sparse matrices
# sliced-based matrices
sparse.lil_matrix(C)
```




    <10x5 sparse matrix of type '<class 'numpy.float64'>'
    	with 26 stored elements in LInked List format>




```python
vector1 = np.array([1, 2, 3])
vector2 = np.array([2, 3, 4])
print(vector1)
```

    [1 2 3]



```python
print(vector2)
```

    [2 3 4]



```python
# Addition of `vector1` and `vector2`
vector3 = vector1 + vector2

# Print `vector3`
print(vector3)
```

    [3 5 7]



```python
# Subtraction of `vector2` and `vector1`
vector4 = vector2 - vector1

# print `vector4`
print(vector4)
```

    [1 1 1]



```python
# Dot product of `vector1` and `vector2`
dotProduct = np.dot(vector1, vector2)

# Print `dotProduct`
print(dotProduct)
```

    20



```python
# Cross product of `vector1` and `vector2`
# vector product in vector algebra; search the formula online
crossProduct = np.cross(vector1, vector2)

# Print `crossProduct`
print(crossProduct)
```

    [-1  2 -1]


## Matrices: Operations and Routines


```python
np.add(vector1, vector2)
```




    array([3, 5, 7])




```python
np.subtract(vector1, vector2)
```




    array([-1, -1, -1])




```python
np.divide(vector1, vector2)
```




    array([ 0.5       ,  0.66666667,  0.75      ])




```python
np.multiply(vector1, vector2)
```




    array([ 2,  6, 12])




```python
# Vector dot product
vectorDotProduct = np.vdot(vector1, vector2)
print(vectorDotProduct)
```

    20



```python
# Inner product
innerProduct = np.inner(vector1, vector2)
print(vectorDotProduct)
```

    20



```python
# Outer product
outerProduct = np.outer(vector1, vector2)
print(vectorDotProduct)
```

    20



```python
matrix1 = np.matrix([[0.47332239, 0.26149519], [0.86380934, 0.01665965]])
matrix2 = np.matrix([[3, 4], [5, 6]])

print(matrix1)
```

    [[ 0.47332239  0.26149519]
     [ 0.86380934  0.01665965]]



```python
print(matrix2)
```

    [[3 4]
     [5 6]]



```python
# Tensor dot product
tensorDotProduct = np.tensordot(matrix1, matrix2)
print(vectorDotProduct)
```

    20



```python
# Kronecker product
kronProduct = np.kron(matrix1, matrix2)
print(vectorDotProduct)
```

    20



```python
print(matrix1)
```

    [[ 0.47332239  0.26149519]
     [ 0.86380934  0.01665965]]



```python
# exponent
linalg.expm(matrix1)
#linalg.expm2(matrix1)
#linalg.expm3(matrix1)
```




    array([[ 1.76478622,  0.34978586],
           [ 1.15546404,  1.15393687]])




```python
# logarithm
linalg.logm(matrix1)
```




    array([[-0.54372715+0.89057597j,  0.24956103-0.77901846j],
           [ 0.82438668-2.57336825j, -0.97954865+2.25101668j]])




```python
# squared root
linalg.sqrtm(matrix1)
```




    array([[ 0.62966832+0.15061317j,  0.21791187-0.1317467j ],
           [ 0.71983850-0.43520505j,  0.24911742+0.38068933j]])




```python
# lambda
linalg.funm(matrix1, lambda x: x*x)
```




    array([[ 0.44991607,  0.12812795],
           [ 0.42325106,  0.22615953]])




```python
# transposition
# make a new matrix whose rows are the columns of the original
matrix1.T
```




    matrix([[ 0.47332239,  0.86380934],
            [ 0.26149519,  0.01665965]])




```python
np.transpose(matrix1)
```




    matrix([[ 0.47332239,  0.86380934],
            [ 0.26149519,  0.01665965]])




```python
# conjugate transposition
# interchanges the row and column index for each matrix element
matrix1.H
```




    matrix([[ 0.47332239,  0.86380934],
            [ 0.26149519,  0.01665965]])




```python
# inverse
# matrix multiplied with the original matrix results in an identity matrix
matrix1.I
```




    matrix([[-0.0764216 ,  1.19953792],
            [ 3.96248993, -2.17123747]])




```python
linalg.inv(matrix1)
```




    array([[-0.0764216 ,  1.19953792],
           [ 3.96248993, -2.17123747]])




```python
# cast an array
matrix1.A
```




    array([[ 0.47332239,  0.26149519],
           [ 0.86380934,  0.01665965]])




```python
# retrieve the trace or sum of the elements on the main matrix diagonal
np.trace(matrix1)
```




    0.48998204000000001




```python
# retrieve the matrix rank or the number
# of Singular Value Decomposition singular values
# of an array that are greater than a certain threshold
np.linalg.matrix_rank(matrix1)
```




    2




```python
# norm of a matrix
# number defined in terms of the entries of the matrix
# how large the elements are
linalg.norm(matrix1)
```




    1.0192438074758199




```python
# matrix determinant
linalg.det(matrix1)
```




    -0.21799660213251107



Solving system of $Ax=b$, where $A$ is a square matrix and $b$ a general matrix. There are two methods to find $x$.


```python
A = np.matrix([[0.35115177, 0.79693272], [0.81264708, 0.06853826]])
b = np.matrix([[1.+5.j, 0.+2.j, 0.+3.j], [ 0.+4.j, 0.+5.j, 0.+6.j]])
print(A)
```

    [[ 0.35115177  0.79693272]
     [ 0.81264708  0.06853826]]



```python
print(b)
```

    [[ 1.+5.j  0.+2.j  0.+3.j]
     [ 0.+4.j  0.+5.j  0.+6.j]]



```python
# Dense matrix solver
linalg.solve(A, b)
```




    array([[-0.10991486+4.56259221j,  0.00000000+6.17037842j,
             0.00000000+7.33850519j],
           [ 1.30324276+4.26364433j,  0.00000000-0.20922633j,
             0.00000000+0.53087407j]])




```python
F = np.matrix([[0., 1., 0.], [0., 0., 1.], [0., 0., 0.]])
E = np.matrix([[1],[2],[3]])
print(F)
```

    [[ 0.  1.  0.]
     [ 0.  0.  1.]
     [ 0.  0.  0.]]



```python
print(E)
```

    [[1]
     [2]
     [3]]



```python
# Linear least-square solver
np.linalg.lstsq(F,E)
```




    (matrix([[ 0.],
             [ 1.],
             [ 2.]]),
     matrix([], shape=(1, 0), dtype=float64),
     2,
     array([ 1.,  1.,  0.]))



For sparse matrices, `linalg.spsolve()`may solve the equation, otherwise, it might still be possible to obtain an approximate $x$ with the help of the `linalg.lstsq()`.

# Eigenvalues and Eigenvectors

The eigenvalues and eigenvectors are important concepts in many computer vision and machine learning techniques:

- Principal Component Analysis (PCA) for dimensionality reduction.
- EigenFaces for [face recognition](http://scikit-learn.org/stable/auto_examples/applications/face_recognition.html). Consult the latter case for an illustration.

Almost all vectors change direction, when they are multiplied by a matrix. However, certain resulting vectors maintain the same direction after the multiplication. These are the eigenvectors.

Multiply an eigenvector by a matrix, and the resulting vector of that multiplication is equal to a multiplication of the original eigenvector with $\lambda$, the eigenvalue:

$$Ax = \lambda x$$

Eigenvalue gives valuable information: whether one of the eigenvectors is stretched, shrunk, reversed, or left unchanged when multiplied by a matrix.


```python
myMatrix = np.matrix([[0.84790079, 0.08996585], [0.66653841, 0.94212726]])
print(myMatrix)
```

    [[ 0.84790079  0.08996585]
     [ 0.66653841  0.94212726]]



```python
# Solve eigenvalue problem
la, v = linalg.eig(myMatrix) 

# Unpack eigenvalues
l1, l2 = la

# First eigenvector
v[:,0]
```




    array([-0.40641758,  0.91368745])




```python
# Second eigenvector
v[:,1]
```




    array([-0.29036942, -0.95691463])




```python
# Or unpack eigenvalues with `eigvals()`
linalg.eigvals(myMatrix)
```




    array([ 0.64564412+0.j,  1.14438393+0.j])




```python
# laternative
eigvals(myMatrix)
```




    array([ 0.64564412,  1.14438393])



With sparse matrices, `la, v = sparse.linalg.eigs(myMatrix,1)`; the number of eigenvalues and eigenvectors that has to be retrieved = 1.

# Singular Value Decomposition (SVD)

SVD is useful for many tasks:

- data compression,
- noise reduction, and
- data analysis.

SVD is closely linked to Principal Component Analysis (PCA), which is used for dimensionality reduction.

Another link is one with data mining and natural language processing (NLP): Latent Semantic Indexing (LSI). It is a technique that is used in document retrieval and word similarity. Latent semantic indexing uses SVD to group documents to the concepts that could consist of different words found in those documents. Various words can be grouped into a concept. Also here, SVD reduces the noisy correlation between words and their documents, and it decreases the number of dimensions that the original data has.


The singular value decomposition of a matrix $A$ is the decomposition or factorization of $A$ into the product of three matrices: $A=U∗Σ∗V^t$.

The size of the individual matrices is as follows given the matrix $A$ is of size $M x N$:

- Matrix $U$ is of size $M x M$
- Matrix $V$ is of size $N x N$
- Matrix $\Sigma$ is of size $M x N$

The $∗$ indicates that the matrices are multiplied and the $t$ in $V^t$ 
means that the matrix is transposed, which means that the rows and columns are interchanged.

Simply stated, singular value decomposition provides a way to break a matrix into simpler, meaningful pieces. These pieces may contain some data we are interested in.


```python
print(myMatrix)
```

    [[ 0.84790079  0.08996585]
     [ 0.66653841  0.94212726]]



```python
# Singular Value Decomposition
U,s,Vh = linalg.svd(myMatrix) 

# Initialize `M` and `N`
M,N = myMatrix.shape

# Construct sigma matrix in SVD
Sig = linalg.diagsvd(s,M,N)
```


```python
print(U)
print(s)
print(Vh)
```

    [[-0.53763961 -0.84317474]
     [-0.84317474  0.53763961]]
    [ 1.32147227  0.5591224 ]
    [[-0.7702571  -0.63773348]
     [-0.63773348  0.7702571 ]]



```python
print(M)
print(N)
```

    2
    2



```python
print(Sig)
```

    [[ 1.32147227  0.        ]
     [ 0.          0.5591224 ]]


With sparse matrices, use the `sparse.linalg.svds()`.

## Compress images with SVD


```python
%matplotlib inline
# Import the necessary packages
import numpy as np
from scipy import linalg
from skimage import data
import matplotlib.pyplot as plt
```


```python
# Get an image from `skimage`
img = data.camera()

print(img)
print(img.shape)
```

    [[156 157 160 ..., 152 152 152]
     [156 157 159 ..., 152 152 152]
     [158 157 156 ..., 152 152 152]
     ..., 
     [121 123 126 ..., 121 113 111]
     [121 123 126 ..., 121 113 111]
     [121 123 126 ..., 121 113 111]]
    (512, 512)



```python
fig = plt.figure(figsize=(8, 3))
ax = fig.add_subplot(121)
ax.imshow(img, cmap='gray')
plt.show()
```


![png](img/vectors_and_arrays/output_136_0.png)



```python
# Check number of singular values
linalg.svdvals(img)
```




    array([  6.38689996e+04,   1.44910897e+04,   1.09561592e+04,
             6.19958837e+03,   5.85460599e+03,   4.82514545e+03,
             4.59023130e+03,   3.61148738e+03,   3.34731861e+03,
             3.14349896e+03,   3.05262875e+03,   2.95922014e+03,
             2.84709763e+03,   2.81972262e+03,   2.53580358e+03,
             2.35379736e+03,   2.25234388e+03,   2.19445315e+03,
             1.95347281e+03,   1.93643231e+03,   1.78576072e+03,
             1.68444543e+03,   1.55985334e+03,   1.53124809e+03,
             1.49461049e+03,   1.46783730e+03,   1.37841479e+03,
             1.31705840e+03,   1.28469563e+03,   1.26983772e+03,
             1.23258950e+03,   1.19028553e+03,   1.14311122e+03,
             1.11896715e+03,   1.07893598e+03,   1.04322585e+03,
             1.00915095e+03,   9.95390582e+02,   9.77961424e+02,
             9.41174385e+02,   9.32201249e+02,   8.93615745e+02,
             8.74195561e+02,   8.58051291e+02,   8.29598226e+02,
             8.00811160e+02,   7.93729536e+02,   7.89373695e+02,
             7.58404767e+02,   7.29609262e+02,   7.09087154e+02,
             7.00077886e+02,   6.86673719e+02,   6.65400930e+02,
             6.56677192e+02,   6.28475541e+02,   6.10557098e+02,
             5.94000126e+02,   5.84294112e+02,   5.72429055e+02,
             5.69451585e+02,   5.50921578e+02,   5.37266578e+02,
             5.33291637e+02,   5.21789437e+02,   5.05141703e+02,
             5.01052645e+02,   4.93184398e+02,   4.80118682e+02,
             4.73384191e+02,   4.56418309e+02,   4.48913305e+02,
             4.44146447e+02,   4.32995274e+02,   4.26315380e+02,
             4.22328895e+02,   4.05541490e+02,   3.98653047e+02,
             3.96319140e+02,   3.89453125e+02,   3.84647691e+02,
             3.75627016e+02,   3.71488605e+02,   3.67691102e+02,
             3.59979435e+02,   3.50653860e+02,   3.48018191e+02,
             3.35741100e+02,   3.33256260e+02,   3.26076697e+02,
             3.19055085e+02,   3.09630221e+02,   3.03809793e+02,
             3.02834775e+02,   2.94473792e+02,   2.89237544e+02,
             2.83072764e+02,   2.80221278e+02,   2.74752660e+02,
             2.71946305e+02,   2.67137796e+02,   2.63076632e+02,
             2.56422198e+02,   2.54502372e+02,   2.49312761e+02,
             2.44629388e+02,   2.42104483e+02,   2.38784276e+02,
             2.24177802e+02,   2.21962143e+02,   2.20585254e+02,
             2.16305370e+02,   2.14023345e+02,   2.10191299e+02,
             2.06326744e+02,   2.01216165e+02,   1.95901568e+02,
             1.93425008e+02,   1.86544957e+02,   1.81946842e+02,
             1.81111952e+02,   1.79250161e+02,   1.73406209e+02,
             1.71851416e+02,   1.68149855e+02,   1.61459003e+02,
             1.60960447e+02,   1.54019279e+02,   1.52120965e+02,
             1.50570121e+02,   1.45586776e+02,   1.42319905e+02,
             1.41079625e+02,   1.39402001e+02,   1.36894791e+02,
             1.35479523e+02,   1.33651596e+02,   1.29473707e+02,
             1.25074480e+02,   1.23799569e+02,   1.21554208e+02,
             1.19267845e+02,   1.16142251e+02,   1.14798303e+02,
             1.09566347e+02,   1.07809839e+02,   1.05206661e+02,
             1.03096542e+02,   1.02101366e+02,   9.92918020e+01,
             9.80967375e+01,   9.25471187e+01,   9.06671721e+01,
             8.94885949e+01,   8.59407127e+01,   8.47271098e+01,
             8.25043759e+01,   8.05678329e+01,   7.98244891e+01,
             7.88264924e+01,   7.60557363e+01,   7.52551314e+01,
             7.20841101e+01,   7.16497267e+01,   7.09295551e+01,
             6.93447334e+01,   6.68699361e+01,   6.61087591e+01,
             6.51986683e+01,   6.19754992e+01,   6.03605056e+01,
             5.93183446e+01,   5.72723667e+01,   5.62244673e+01,
             5.48748626e+01,   5.35303251e+01,   5.31190637e+01,
             5.14073607e+01,   5.05882613e+01,   4.85873327e+01,
             4.77033490e+01,   4.61730309e+01,   4.58253352e+01,
             4.45738941e+01,   4.41688671e+01,   4.30565443e+01,
             4.21824960e+01,   4.13096543e+01,   4.01687931e+01,
             3.89251008e+01,   3.76938723e+01,   3.71696405e+01,
             3.65261279e+01,   3.63225111e+01,   3.47286204e+01,
             3.38767247e+01,   3.36300965e+01,   3.28077851e+01,
             3.22430013e+01,   3.19168059e+01,   3.04258560e+01,
             3.01029523e+01,   2.94482797e+01,   2.93136739e+01,
             2.84675969e+01,   2.70583102e+01,   2.69171207e+01,
             2.62988906e+01,   2.53912737e+01,   2.52678982e+01,
             2.48858839e+01,   2.35476097e+01,   2.33100666e+01,
             2.23100190e+01,   2.15793552e+01,   2.11961369e+01,
             2.05803331e+01,   2.00864770e+01,   1.96897799e+01,
             1.84825965e+01,   1.78147513e+01,   1.76346865e+01,
             1.67939919e+01,   1.64216226e+01,   1.60543495e+01,
             1.55344956e+01,   1.49332344e+01,   1.45289863e+01,
             1.42587318e+01,   1.37963455e+01,   1.34972766e+01,
             1.34093515e+01,   1.22216082e+01,   1.19781514e+01,
             1.15231001e+01,   1.09781821e+01,   1.09187142e+01,
             1.03661279e+01,   1.00838177e+01,   9.79683858e+00,
             9.54913700e+00,   9.35377121e+00,   8.98307957e+00,
             8.62827079e+00,   8.43304143e+00,   8.21026198e+00,
             8.11055326e+00,   7.84205214e+00,   7.82091983e+00,
             7.72211462e+00,   7.65176844e+00,   7.57527347e+00,
             7.48948062e+00,   7.32714219e+00,   7.24843636e+00,
             7.23134018e+00,   7.11545722e+00,   6.94245132e+00,
             6.90872672e+00,   6.89105932e+00,   6.85271365e+00,
             6.73119810e+00,   6.67101027e+00,   6.65355095e+00,
             6.61537333e+00,   6.57919154e+00,   6.51264665e+00,
             6.43529244e+00,   6.38642585e+00,   6.32124352e+00,
             6.26921968e+00,   6.22470192e+00,   6.18684862e+00,
             6.12487899e+00,   6.08056310e+00,   6.02142397e+00,
             5.98369919e+00,   5.96324230e+00,   5.90521877e+00,
             5.89164599e+00,   5.85948724e+00,   5.78142589e+00,
             5.77436927e+00,   5.72763143e+00,   5.68593121e+00,
             5.64079641e+00,   5.59691503e+00,   5.57872232e+00,
             5.56560739e+00,   5.46793402e+00,   5.45802649e+00,
             5.43835398e+00,   5.40609891e+00,   5.38649282e+00,
             5.35337487e+00,   5.32541786e+00,   5.26717335e+00,
             5.22386437e+00,   5.18279263e+00,   5.15811624e+00,
             5.11921277e+00,   5.07521779e+00,   5.06576107e+00,
             5.02393795e+00,   4.98303961e+00,   4.93214693e+00,
             4.91731420e+00,   4.85042743e+00,   4.84257910e+00,
             4.82282191e+00,   4.80521779e+00,   4.75593168e+00,
             4.74270318e+00,   4.70514352e+00,   4.68191260e+00,
             4.65822179e+00,   4.62781009e+00,   4.58206294e+00,
             4.55433009e+00,   4.52197896e+00,   4.47442964e+00,
             4.45449682e+00,   4.45025349e+00,   4.38840686e+00,
             4.38117331e+00,   4.35291236e+00,   4.32921175e+00,
             4.30202225e+00,   4.26791973e+00,   4.21523395e+00,
             4.21145347e+00,   4.18818581e+00,   4.17622715e+00,
             4.13550887e+00,   4.12577916e+00,   4.11039284e+00,
             4.09685513e+00,   4.07109036e+00,   4.02939243e+00,
             4.00331783e+00,   3.97696241e+00,   3.94503312e+00,
             3.93368480e+00,   3.84158980e+00,   3.82521909e+00,
             3.80125077e+00,   3.76970168e+00,   3.76023660e+00,
             3.75084950e+00,   3.73636863e+00,   3.72902284e+00,
             3.66340067e+00,   3.64716250e+00,   3.61147057e+00,
             3.60098533e+00,   3.58812743e+00,   3.53498132e+00,
             3.52033176e+00,   3.49043477e+00,   3.46514179e+00,
             3.44527900e+00,   3.42356869e+00,   3.40704111e+00,
             3.34890626e+00,   3.32804671e+00,   3.29605788e+00,
             3.28071188e+00,   3.25011320e+00,   3.23532434e+00,
             3.21811867e+00,   3.18616262e+00,   3.16750232e+00,
             3.12643543e+00,   3.10574635e+00,   3.09627820e+00,
             3.05806788e+00,   3.01996318e+00,   3.00220202e+00,
             2.95796156e+00,   2.94847475e+00,   2.90728643e+00,
             2.87763724e+00,   2.86278424e+00,   2.83268253e+00,
             2.82204155e+00,   2.80120062e+00,   2.78503941e+00,
             2.76435415e+00,   2.74332238e+00,   2.71836658e+00,
             2.71569528e+00,   2.69770561e+00,   2.64760980e+00,
             2.62849348e+00,   2.61505591e+00,   2.59158684e+00,
             2.54179224e+00,   2.51940320e+00,   2.50792107e+00,
             2.49862874e+00,   2.48957871e+00,   2.44314028e+00,
             2.42365590e+00,   2.41973257e+00,   2.35331088e+00,
             2.34517297e+00,   2.31817739e+00,   2.30469350e+00,
             2.27487356e+00,   2.26056150e+00,   2.23148661e+00,
             2.20462740e+00,   2.19470644e+00,   2.17251816e+00,
             2.14874503e+00,   2.11092460e+00,   2.10652682e+00,
             2.06180197e+00,   2.03489164e+00,   2.02493153e+00,
             2.01580398e+00,   1.97923652e+00,   1.95861598e+00,
             1.92322853e+00,   1.91765275e+00,   1.88301850e+00,
             1.87107658e+00,   1.86174602e+00,   1.81490812e+00,
             1.80252752e+00,   1.78513146e+00,   1.75186936e+00,
             1.73384237e+00,   1.69815585e+00,   1.67087083e+00,
             1.65504461e+00,   1.62833826e+00,   1.59350016e+00,
             1.58518520e+00,   1.57406121e+00,   1.52318355e+00,
             1.52041380e+00,   1.48200585e+00,   1.46617961e+00,
             1.46038913e+00,   1.44102572e+00,   1.42057616e+00,
             1.40485251e+00,   1.38762119e+00,   1.37527086e+00,
             1.36211908e+00,   1.34039135e+00,   1.29930779e+00,
             1.26872251e+00,   1.23195908e+00,   1.22788520e+00,
             1.22080800e+00,   1.19465263e+00,   1.17805481e+00,
             1.16555637e+00,   1.12718364e+00,   1.10793283e+00,
             1.10594246e+00,   1.06675455e+00,   1.04439770e+00,
             1.02978244e+00,   1.00620518e+00,   9.81504353e-01,
             9.57163454e-01,   9.33625951e-01,   9.08940260e-01,
             8.89946907e-01,   8.73754378e-01,   8.54367286e-01,
             8.33089642e-01,   8.14710711e-01,   7.90545224e-01,
             7.44180512e-01,   7.25739820e-01,   7.18590163e-01,
             6.97220443e-01,   6.39175669e-01,   6.18528497e-01,
             5.96683219e-01,   5.83800689e-01,   5.72232599e-01,
             5.31453332e-01,   5.26804142e-01,   5.20281933e-01,
             4.75313705e-01,   4.54635778e-01,   4.34567930e-01,
             4.23330255e-01,   4.04104582e-01,   3.84718206e-01,
             3.61246016e-01,   3.32050389e-01,   2.95766519e-01,
             2.84756495e-01,   2.66739045e-01,   2.41418262e-01,
             2.08111390e-01,   1.85992093e-01,   1.48587324e-01,
             1.32123996e-01,   1.16957628e-01,   8.67857990e-02,
             7.80847492e-02,   6.61861872e-02,   4.85935027e-02,
             3.31185916e-02,   1.08448303e-02])




```python
# Singular Value Decomposition
U, s, Vh = linalg.svd(img)

# Use only 32 singular values
A = np.dot(U[:,0:32], 
          np.dot(np.diag(s[0:32]), Vh[0:32,:]))
```


```python
fig = plt.figure(figsize=(8, 3))
print(fig)
```

    Figure(576x216)



    <matplotlib.figure.Figure at 0x7f7bbb7b0710>



```python
# Add a subplot to the figure
ax = fig.add_subplot(121)
print(ax)
```

    Axes(0.125,0.125;0.352273x0.755)



```python
fig = plt.figure(figsize=(8, 3))

# Add a subplot to the figure
ax = fig.add_subplot(121)

# Plot `img` on grayscale
ax.imshow(img, cmap='gray')

# Add a second subplot to the figure
ax2 = fig.add_subplot(122)

# Plot `A` in the second subplot
ax2.imshow(A)

# Add a title
fig.suptitle('Image Compression with SVD', fontsize=14, fontweight='bold')

# Show the plot
plt.show()
```


![png](img/vectors_and_arrays/output_141_0.png)

