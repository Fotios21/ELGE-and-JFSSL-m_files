# ELGE-and-JFSSL-m_files
Subspace Learning and Feature Selection via Orthogonal Mapping

Matlab code for Subspace Learning and Feature Selection


Popular dimensionality reduction (DR) algorithms 
within Expanded Linear Extension of Graph Embedding (ELGE) and
Joint Feature Selection and Subspace Learning (JFSSL) frameworks are 
implemented as Matlab m-files and tested in the experiments 
conducted on Georgia Tech Face data set. 

The code refers to the paper: 

F.D. Mandanas and C.L. Kotropoulos, "Subspace Learning and Feature 
Selection via Orthogonal Mapping", IEEE Transactions on Signal Processing, vol. 68, pp. 1034-1047, 2020.
DOI: 10.1109/TSP.2020.2967714

There are four folders.
Folder Georgia_Tech_dataset_cropped_faces contains cropped faces of Georgia Tech face data set. Details are given below.
Folder ELGE contains 18 DR algorithms within ELGE framework. 
Folder JFSSL contains the same 18 DR algorithms within JFSSL framework.
Folder utils contains necessary m-files for the implementation of ELGE and JFSSL frameworks. 

The 18 DR algorithms are the following:
1. Principal Component Analysis (PCA)
2. Linear Discriminant Analysis (LDA)
3. Orthogonal Linear Discriminant Analysis (OLDA)
4. Neighborhood Preserving Embedding (NPE)
5. Orthogonal Neighborhood Preserving Projections (ONPP)
6. Locality Preserving Projections (LPP)
7. Orthogonal Locality Preserving Projections (OLPP)
8. Isometric Mapping (ISOMAP)
9. Orthogonal Isometric Projection (OIP)
10. Local Tangent Space Alignment (LTSA)
11. Orthogonal Local Tangent Space Alignment (OLTSA)
12. Maximum Margin Criterion (MMC) 
13. Locality Sensitive Discriminant Analysis (LSDA)
14. Local Discriminant Embedding (LDE)
15. Unsupervised Discriminant Projection (UDP)
16. Maximum Margin Projection (MMP) 
17. Semi-supervised Discriminant Analysis (SDA)
18. Baseline: The raw vectors are used, without applying any DR algorithm. 


Georgia Tech face data set comprises images for 50 subjects.
For each individual, there are 15 color images with cluttered 
background taken at resolution 640 x 480 pixels in JPEG format.
The cropped images of Georgia Tech face data set are employed. 
Data can be downloaded from

http://www.aneﬁan.com/research/GTdb_crop.zip

Credits to 
Ara Nefian

Chen, L., Man, H., & Nefian, A. V. (2005). 
Face recognition based on multi-class mapping of Fisher scores. 
Pattern Recognition, 38(6), 799-811.


The cropped images were resized to 32 × 32 pixels. 
Consequently, each face image was represented as a 1024-dimensional vector. 

Code refers to the case where the percentage of images for each person
used as training samples is 80%. Thus, 12 of 15 images for person object are 
used as training samples, while the remaining 3 images were exploited for 
testing. This is why each m-file has a name ending with 12_3. 

The training samples are randomly selected in order to learn a 
lower dimensional subspace. Taking into account that the training 
set is randomly chosen, 20 different random realizations of the 
training set take place and the average recognition rate across 
the 20 realizations of the test set is reported.



Part of NPE algorithm within ELGE and JFSSL (ELGE_NPE_12_3.m and JFSSL_NPE_12_3.m) 
was taken from Matlab Toolbox for Dimensionality Reduction, Laurens van der Maaten, Delft University of Technology:

https://lvdmaaten.github.io/drtoolbox/ 

The same holds for ONPP algorithm within ELGE and JFSSL (ELGE_ONPP_12_3.m and JFSSL_ONPP_12_3.m). 

Part of LTSA algorithm within ELGE and JFSSL (ELGE_LTSA_12_3.m and JFSSL_LTSA_12_3.m)
was taken from Matlab Toolbox for Dimensionality Reduction, Laurens van der Maaten, Delft University of Technology:

https://lvdmaaten.github.io/drtoolbox/

The same holds for OLTSA algorithm within ELGE and JFSSL (ELGE_OLTSA_12_3.m and JFSSL_OLTSA_12_3.m).

find.nn finds k nearest neighbors for all datapoints in the dataset and is taken from 
Matlab Toolbox for Dimensionality Reduction, Laurens van der Maaten, Delft University of Technology:

https://lvdmaaten.github.io/drtoolbox/

Maaten, L. V. D., & Hinton, G. (2008). Visualizing data using t-SNE. 
Journal of machine learning research, 9(Nov), 2579-2605.



LGE.m and mySVD.m were taken from 

http://www.cad.zju.edu.cn/home/dengcai/Data/DimensionReduction.html.

LGE.m provides a general framework for graph based subspace learning. 
mySVD.m performs an accelerated singular value decomposition. 

dmatrix.m computes the squared distance matrix.  
         
ELGE_LPP_12_3, ELGE_OLPP_12_3, JFSSL_LPP_12_3 and JFSSL_OLPP_12_3 were slightly modified from the code used in the paper. 
So, minor differences in the reported accuracy might be expected. Final conclusions do not change. 


Important note:

knnclassify() has been replaced with fitcknn() and is no longer supported in newer versions of Matlab. 
For example, Matlab R2018 does not accept knnclassify(). 
If you have newer versions of Matlab, changes should be made in the code as follows:

% comment the following line
c1=knnclassify (Y_test', Y_train', X_labels, 1);
% uncomment the following two lines
% mdl = fitcknn(Y_train', X_labels, 'Distance', 'euclidean', 'NumNeighbors', 1);
% c1 = predict(mdl, Y_test');

Please have a look in ELGE_ONPP_12_3 m-file, where the recommended change has been done. 


M-files tested in MATLAB versions R2013b, R2015a, and R2016b.

Code was written by Fotios D. Mandanas (fmandan@gmail.com) 



