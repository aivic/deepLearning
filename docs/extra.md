# MeanShift

Remember  
How many maximum number of clusters user can pass to MeanShift method?  
A: None  
D: Ideally infinity  
D: 100  
D: 10  

Understand  
What may happen if you keep the bandwidth parameter too small while building MeanShift clustering model?  
A: It may lead to the formation of too many clusters  
D: It may lead to the formation of very less number of clusters  
D: It may destabilize the building of MeanShift clustering.  
D: It may not affect the convergence of clustering process.  

Apply  
What is the runtime complexity of MeanShift clustering when iterated 50 times over 1600 data points?  
A: 128000000  
D: 80000  
D: 2000  
D: 100000  

Analyse
What happens when you set "cluster_all" argument of MeanShift clustering method to False?  
A: All the orphans are assigned to a new cluster with cluster label -1.  
D: All the orphans are assigned to their respective nearest clusters.  
D: All the orphans are assigned to a cluster with maximum number of data points.   
D: All the orphans are assigned to a cluster with minimum number of data points.  

# Birch
Remember  
For what type of data-sets does balanced iterative reducing and clustering using hierarchies algorithm is designed? 
A: Very large data-sets  
D: Large data-sets  
D: Medium data-sets  
D: Small data-sets  

Understand  
What happens in the case of BIRCH clustering, when 59 samples enter on a node with a "branching_factor" of 50?  
A: The parent node is split into 2 new nodes.  
D: The parent node is split into 59 new nodes.  
D: The parent node retains all the samples within existing node.  
D: The parent node excludes any extra samples.  

Apply  
What is the BIRCH's Clustering Features, CF for given datapoints (3,4), (2,6), (4,5), (4,7) and (3,8)?  
A: (5, (16, 30), (54, 190))  
D: (5, (2, 4), (4, 8))  
D: (244, 46, 5)  
D: (5, 46, 244)  

Analyze  
Which of the following command is correct about building a BIRCH clustering model with a "threshold" of 0.1 and "branching_factor" of 50?  
A: sklearn.cluster.Birch(threshold=0.1)  
D: sklearn.cluster.Birch()  
D: sklearn.cluster.BIRCH(threshold=0.1, branching_factor=50)  
D: sklearn.cluster.BIRCH(branching_factor=50)  
