## Test yourself SOLUTIONS 
1. In your jupyter notebook, create new chunk for this question. In this chunk, write a for loop that prints out the first ten powers of 2 starting from 2^0.
```
num_list = range(0,10)
for n in num_list:
    print("2^", n, '=', pow(2,n) )
```
2. In your jupyter notebook, create new chunk for this question. In this chunk, write a function that prints out the first N powers of 2 and returns the last value of that loop. It should take in the number of values "N" as input, and check that N is not larger than 100.   
```
def n_powers(n): 
    # Check that n is of the right type and form
    assert isinstance(n,int),'Input is not an integer'
    assert n >= 0, 'Input needs to be positive'
    assert n <= 100, 'Intput is too large!'
    # Loop over n
    for i in range(0,n):
        val = pow(2,i)
        print("2^", i, '=', val )
    return val
n_powers(100)
```
3. In your jupyter notebook, create new chunk for this question. In this chunk, write out the output to a file called "Powers_of_2.txt" the first 10 powers of 2 starting at 0. You can modify your function from Q2. 
```
def n_powers_file(n, filename): 
    # Check that n is of the right type and form
    assert isinstance(n,int),'Input is not an integer'
    assert n >= 0, 'Input needs to be positive'
    assert n <= 100, 'Intput is too large!'
    f = open(filename, "w")
    # Loop over n
    for i in range(0,n):
        val = pow(2,i)
        line = "2^"+ str(i) + '=' + str(val) + "\n"
        f.write(line)
    f.close()
    return
n_powers_file(10, "Powers_of_2.txt")
```
4. In your jupyter notebook, create new chunk for this question. In this chunk, read in the "data.csv" file again to the df variable. Drop all the rows with "NA" and then write this to a file named "data_filtered.txt". 
```
import pandas as pd
df = pd.read_csv('data/data.csv')
df.dropna(inplace = True) 

f = open("data_filtered.txt", "w")
f.write(df.to_string())
f.close()
```
