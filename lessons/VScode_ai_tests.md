# Test yourself SOLUTIONS
Taken/adapted from:
 
### Data pre-processing
A key part of any bioinformatics research is collecting and pre-processing data. In some of the previous tasks, we read in some datasets and checked/changed missing data. We can do this through the agent/chat mode by writing the prompts that will give us some of the additional checks we would do ourselves. Because you know what should be done (i.e., you've done it yourself before!), this is a productivity short-cut. 
- Make a new folder and copy over the "DatasaurusDozen.txt" from the data wrangling tutorial (https://unsw-binf.github.io/BINF_tut/lessons/python_datafun.html).
- Open that folder to work within it, and as before, manage the "Trust" settings. 
- In the chat prompt, type in a prompt to:
  - Make a python script to read in the "DatasaurusDozen.txt"
  - Printout information about the data like column names, fractions of missing data, what data types are present etc.
  - Output a text file with the mean, standard deviation, and correlations of the data.
- Run the script and check the outputs.

### Q1: How does it compare?
> How does the script and the output compare to yours from Week 4? What prompt(s) worked best? List all the steps/prompts and changes you had to make. 

### Data analysis 
- Copy over the "R_dataviz.Rdata" file from Week 8. Recall this file is in R so there will be some extra/different steps.  
- Prompt the agent/chat to write a second script to read this file in. This script could be an R script, but you might want a notebook/markdown book instead.
- Or, better yet, see if there is a way to convert it to be used in a python/jupyter notebook.
- Write a few prompts to answer all the questions and analysis for your Week 8 output.  

### Q2: How does it compare?
> How does the script and the output compare to yours from Week 8? What prompt(s) worked best? List all the steps/prompts and changes you had to make. How easy was it to do the analysis compared to before, knowing what you had to do?  


### Q3: What other analysis can you do - dataset X? 
> Think of three additional things you might want to do with dataset X that you do not know how to do (or have not done before). Write the prompts to do this. How would you check that the outputs are correct? 

### Q4: What other analysis can you do - dataset Y? 
> Think of three additional things you might want to do with dataset Y that you do not know how to do (or have not done before). Write the prompts to do this. How would you check that the outputs are correct here?  

 
### Gene set enrichment pipeline 
One standard analysis pipeline is gene set enrichment from a differential expression experiment. 
Gene set enrichment (GSE) is a method to identify properties of genes or proteins that are over-represented. GSE is a (relatively) straightforward method to sumamrize the results of your experiment, in particular when you believe there is some link or association to a known phenotype (e.g., enrichment for dopamine receptors in Parkinson's disease). It uses statistical approaches to identify significantly enriched groups of genes, and the main annotation database is the Gene Ontology ([GO](http://www.geneontology.org/)) and the Molecular Signatures database ([MSigDB](http://software.broadinstitute.org/gsea/msigdb/index.jsp)). The most well known method is GSEA: http://www.pnas.org/content/102/43/15545.short, but it can be a little complicated to interpret (old dispute here https://www.ncbi.nlm.nih.gov/pubmed/20048385).
For this part, we are going to get our agent/chat to read in, tidy up and analyse an RNA-seq experiment. We will use data from this paper: https://genome.cshlp.org/content/22/4/602, and work through some of the analyses. 

### Q5: Reproducibility 
1. As before, set up a new folder for this part.
2. Download the RNA-seq dataset from the paper. You can use an agent or do it yourself from the supplement. https://genome.cshlp.org/content/genome/suppl/2012/01/03/gr.130468.111.DC1/Supplemental.Database.primateRNAseq.zip
3. Write prompts to replicate the analysis and plots for Supplementary Figure 5,6 and 7b (similar to Figure 1b). These are gene-expression specific plots.
4. Perform a differential expression analysis. Why is this a good or bad idea?
5. Perform gene set enrichment on the differential analysis. What do you expect to come out of this?   
  

  

