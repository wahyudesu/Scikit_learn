# Scikit_learn
Reduksi dimensi dengan PCA


Techniques to Perform Feature Decomposition i use: 
PCA (sklearn.decomposition.PCA)

```
import numpy as np

def PCA(X , num_components):

    # 1: Subtracting the mean of each variable
    X_meaned = X - np.mean(X , axis = 0)

    # 2: Calculating the Covariance Matrix
    cov_mat = np.cov(X_meaned , row var = False)

    # 3: COmpute the EigenValues and Eigenvectors
    eigen_values , eigen_vectors = np.linalg.eigh(cov_mat)

    # 4: Sort Eigenvalues in their descending order
    sorted_index = np.argsort(eigen_values)[::-1]
    sorted_eigenvalue = eigen_values[sorted_index]
    sorted_eigenvectors = eigen_vectors[:,sorted_index]

    # 5: Select a subset from the rearranged Eigenvalue matrix
    eigenvector_subset = sorted_eigenvectors[:,0:num_components]

    # 6: Transforming the data
    X_reduced = np.dot(eigenvector_subset.transpose() , X_meaned.transpose() ).transpose()

    return X_reduced
```
