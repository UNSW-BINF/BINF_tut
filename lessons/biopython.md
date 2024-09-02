# Week 5: Biopython and assignment help 
Adapted from https://biopython.org/docs/1.75/api/Bio.Entrez.html
 
## Objectives 
This week's tutorial is on biopython. You will learn: 
- How to access and manipulate data from different databases 

## Setting up
Start a new notebook. Save the file as "yourname_week5.ipynb". 
As before, copy the code into your notebook as chunks. 

## Biopython
Biopython is a set of freely available tools for biological computation written in Python by an international team of developers.
It is a distributed collaborative effort to develop Python libraries and applications which address the needs of current and future work in bioinformatics. 
Quick install: 

```
pip install biopython
```
Then import into your notebook (or console/terminal or script):

```
import Bio
```
There is a lot of functionality in [biopython](https://biopython.org/docs/ ) (too much to cover here) but revolve around sequences and sequence analysis. 
These include BLAST searches, downloading sequences from NCBI, Phylogenetics, Cluster analysis, Graphics, etc. 
The most useful function is accessing NCBI through their e-utils API. 
Some extra tutorials here: https://biopython-tutorial.readthedocs.io/en/latest/notebooks/00%20-%20Tutorial%20-%20Index.html#  *NOTE: these will be important for your assigmment...*   

### Sequences 
```
from Bio.Seq import Seq

my_seq = Seq("CATGTAGACTAG")

# print out some details about it
print("seq %s is %i bases long" % (my_seq, len(my_seq)))
```

### Reading and writing Sequence Files
Use the SeqIO module for reading or writing sequences as SeqRecord objects.
```
from Bio import SeqIO
from Bio.Seq import Seq
from Bio.SeqRecord import SeqRecord

record = SeqRecord(
    Seq("MKQHKAMIVALIVICITAVVAALVTRKDLCEVHIRTGQTEVAVF"),
    id="YP_025292.1",
    name="HokC",
    description="toxic membrane protein, small",
)
print(record)
# As Genbank entry
Bio.SeqIO.write(record, "HokC.gbk", "gb")
# As FASTA file 
Bio.SeqIO.write(record, "HokC.fasta", "fasta")
```
Other formats here: 
- https://biopython.org/wiki/SeqIO


### Using E-utils
```
from Bio import Entrez
Entrez.email = "my.email@unsw.edu.au"
Entrez.tool = "my_script.py"
```
The general use of e-utils is one of these functions: 
- esearch: searching a database with a query
- efetch: fetching a record from a database with an key/ID
- elink: cross-searching database with an ID

Each function is broadly run like so, where the search returns a "handle", and you read the records/data fromt that handle in. Note, as before, you can only read in the stream once, and will have to repeat the function call if you do not store the record.   
```  
handle = Entrez.esearch(db="XXX", term=query)
record = Entrez.read(handle)
```
  
Searching:
Take a look at the website for different databases and queries you can use. 
E.g., Searching for the human taxonomic ID
```  
handle = Entrez.esearch(db="taxonomy", term="Human")
record = Entrez.read(handle)
len(record)
print(record['IdList'])
taxid = record['IdList'][0]
```

Fetching:
Now we have the ID/key for the term we want. We can then retreive that entry from the taxonomy database using that ID.

```
handle = Entrez.efetch(db="taxonomy", id=taxid, retmode="xml")
record = Entrez.read(handle)
```

The record that we read in from the search handle is a list. We access each result using an index.
e.g., 

```
first_result = record[0]
```

And for multiple results, we can iterate through:
```
for result in record:
    print(result)
```

The results from this search are individual dictionaries, so we can view the data through keys() and values(). 
```
print(first_result.keys())
print(first_result.values())
```

And then retrieve individual results based on keys. For Taxonomic entries, some of these inlcude: 
```
print(first_result['ScientificName'])
print(first_result['Lineage'])
```
 
Cross IDs search:
Now, sometimes we have the key from once database and want the ID from a second. We can do this with the elink function.  
```
handle = Entrez.elink(dbfrom="taxonomy", db="assembly", from_uid=taxid)
links = Entrez.read(handle)
```

How many assembly entries do we get for the human taxon? 
As before, we first access the first entry, and then the set of links, and final the ids. It is a little convoluted because of the list -> dict -> list -> dict structure of the results.  
```
len(links[0]['LinkSetDb'][0]['Link'] ) 
```

Let's take the first result, and access the record in the assembly database. 
```
assembly_id = links[0]['LinkSetDb'][0]['Link'][0]['Id']
handle = Entrez.efetch(db="assembly", id=assembly_id, retmode="xml")
record = Entrez.read(handle)
print(record)
```

As you can see, not much in that! Let's use the taxid ID to search for other database entries, and once again select the first ID. 
```
handle = Entrez.elink(dbfrom="assembly", db="nuccore", from_uid=assembly_id)
links = Entrez.read(handle)
nuc_id = links[0]['LinkSetDb'][0]['Link'][0]['Id']
handle = Entrez.efetch(db="nuccore", id=nuc_id, retmode="xml")
record = Entrez.read(handle)
print(record)
```
What does this give us? A random region of the genome?!


You can refine your queries by selecting certain fields aswell. For example, this search looks for organisms with the human taxid, and filters on "RefSeq" entries and with the word "CYBB" in the record title.  
```
handle = Entrez.esearch(db="nuccore", term="txid"+str(taxid)+"[Organism] AND refseq[filter] AND CYBB[title]")
record = Entrez.read(handle)
nuc_id = record['IdList'][0]
handle = Entrez.efetch(db="nuccore", id=nuc_id, retmode="xml")
record = Entrez.read(handle)
print(record)
```
What does this give us? 


More here: 
https://biopython.org/docs/1.75/api/Bio.Entrez.html
