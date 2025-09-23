## Test yourself SOLUTIONS
1. In your jupyter notebook, create new chunk for this question. In this chunk, write some code where you assign your name to a variable called user. Then print out a sentence that reads "This is my NAME codebook", where NAME is replaced by your user text.
```
user = "Sara"
print( "This is my ", user, " codebook")
print( f"This is my {user} codebook")
```

2. In your jupyter notebook, create new chunk for this question. In this chunk, start off by importing the "random" python package (i.e., import random). Then, write some code that assigns a random number to two variables (x and y) with the random.random() function. Then calculate the average value of these variables (x and y), and round the result to the nearest two decimal points. Assign that result to the variable z, and print it out.
```
import random
import math
random.random()
x = random.random() 
y = random.random() 
z = (x+y)/2
print( round(z,2))
```

3. In your jupyter notebook, create new chunk for this question. In this chunk, copy the gene_list variable from the previous code to a new variable called gene_list_test. Add three random genes and remove the third gene in the list. Add a gene to the middle of the list.

```
gene_list = ["DDX11L1","WASH7P","MIR6859-1","MIR1302-2HG","MIR1302-2","FAM138A"]
gene_list_test = gene_list.copy() 

gene_list_test.append([]"BRCA2", "DMR5", "TAF1"]) 
gene_list_test.remove("MIR6859-1")

mid_i = (len(gene_list_test) )/2 
gene_list_test.insert(mid_i, "IGFBP3")
```

4. In your jupyter notebook, create new chunk for this question. Create a dictionary for gene expression of multiple genes for multiple samples. Call it gene_exp_dict. 
```
gene_exp_dict = {"RAC1P":[0,8,9,0,1],"HM13":[0,5,6,7,9],"RPSAP9":[3,0,1,9,0],"MIR32":[5,0,3,5,6],"GTF3C2":[0,6,2,5,67],"RBPMS":[0,5,43,2,1],"MTHFSD":[0,9,8,0,4],"SCD5":[0,4,4,5,76], "CALM1P2":[0,2,2,4,5,6]}
```
Populate the dictionary with at least 10 genes for 5 samples.
```
gene_exp_dict["WASH7P"] = [1,5,6,1,2]
print(gene_exp_dict["WASH7P"]) 
gene_exp_dict["HM13"]  = [0,0,0,0,1]
gene_exp_dict["MIR32"]  = [10,21,34,0,41]

print(gene_exp_dict.keys())
print(gene_exp_dict.values())

```
Write the code to get the gene expression for the 4th gene, 2nd sample.
```
print(gene_exp_dict["MIR32"][1]) 
genes = list(gene_exp_dict.keys())
gene_target = genes[3]
sample_target = 1 
print(gene_exp_dict[gene_target][sample_target])
```


Now these are obviously not the only (nor best!) solutions. 
Feel free to share yours as comments or issues or reviews on the github. 
