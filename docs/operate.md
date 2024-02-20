# Operate

The operate step is the most powerful but also the hardest step to learn. It lets you take any data and perform a series of sequential OPERATEs on it. These OPERATEs are simple but when combined together can acheive complex behaviour.

Most OPERATEs can be performed on single and multicolumn data but some OPERATEs only work on single column data. Some operate functions are also denoted as **finishing** this is because the data they output cannot be operated on and can only be used in steps such as Snapshot and Export.

You are also not limited to how many operate steps you can perform. However, each operate step will need a new name otherwise the data will be overwritten.

## Anatomy
All operate steps follow the same syntax
```
OPERATE (Name) Data_Name FUNC1(args) FUNC2(args) ... 
```

## Function types

### Chainable (C)
These are functions that produce operable data, this is data that can be used in another process

### Non-Chainable (N)
These are functions that produce operable data, this is data that can be used in another process

### Single Column (S)
These functions will only work if the data input has a single column, therefore these functions will not work with data from a TABLE OPERATE.

### Flexible (F)
These functions work with both single and multicolumn data

## Functions
The functions execute sequentially from left to right, each has a name identifier and an argument input


### Add (C,S)

The add function adds any number to all values in a table

``` sql
OPERATE (...) ... ADD(Value)
```
```
ADD(10)
```
```
t  |  Signal         t  |  Signal
---|--------         ---|--------
1  |      10   -->   1  |      20
2  |       5         2  |      15    
```

### Subtract (C,S)

The subract function subtracts any number from values in a table

``` sql
OPERATE (...) ... SUBTRACT(Value)
```
```
SUBTRACT(10)
```
```
t  |  Signal         t  |  Signal
---|--------         ---|--------
1  |      10   -->   1  |       0
2  |       5         2  |      -5    
```

### Multiply (C,S)

The divide function divides all values in table

``` sql
OPERATE (...) ... MULTIPLY(Value)
```
```
MULTIPLY(10)
```
```
t  |  Signal         t  |  Signal
---|--------         ---|--------
1  |      10   -->   1  |     100
2  |       5         2  |      50    
```

### Divide (C,S)

The divide function divides all values in table

``` sql
OPERATE (...) ... DIVIDE(Value)
```
```
DIVIDE(10)
```
```
t  |  Signal         t  |  Signal
---|--------         ---|--------
1  |      10   -->   1  |       1
2  |       5         2  |     0.5    
```

### Rename Column (C,S)
``` sql
OPERATE (...) ... RENAME(Name)
```
```
RENAME(New_Signal)
```
```
t  |  Signal         t  |  New_Signal
---|--------         ---|------------
1  |      10   -->   1  |          10
2  |       5         2  |           5    
```  


### Resample (C,F)
Resamples the data to meet a specified time frequency, has a variety of methods for resampling the data
``` sql
OPERATE (...) ... RESAMPLE(time,method)
```
Resampling Methods
#### Max
Gets max value from each resampled window

#### Min
Gets min value from each resampled window

#### Mean
Gets mean value from each resampled window


#### Sum
Sums all values in resampling window


### Remove Gaps (C,F)

``` sql
OPERATE (...) ... DROPGAP()
```
```
DROPGAP()
```
```
t  |  Signal         t  |  Signal
---|--------         ---|--------
1  |      10   -->   1  |      10
2  |     NaN         3  |       5
3  |       5           
```  
```
DROPGAP()
```
``` 
t  |  one|  two         t  |  one|  two
---|-----|-----         ---|-----|-----
1  |   10|  NaN   -->   3  |    5|    3
2  |  NaN|    7         
3  |    5|    3         
```  

### Fill Gaps (C,F)
Fills gaps in data with a specified value
``` sql
OPERATE (...) ... FILLGAP(value)
```

### Forward Fill Gaps (C,F)
Fills gaps with previously found data, will fill an unlimited amount of gaps after a data point. If specified can limit the fill reach
``` sql
OPERATE (...) ... FFILL(number?)
```

### Back Fill Gaps (C,F)
Fills gaps with values ahead if found, will fill an unlimited amount of gaps before a data point. If specified can limit the fill reach
``` sql
OPERATE (...) ... BFILL(number?)
```

### Interpolate (C,F)
Fills gaps using linear interpolation between existing data points and gaps
``` sql
OPERATE (...) ... INTERPOLATE(number?)
```

### Maximum (C,F)
If no number specified, Number will default to 1

``` sql
OPERATE (...) ... MAX(Number?)
```
```
MAX(2)
```
```
t  |  Signal         t  |  Signal
---|--------         ---|--------
1  |      10   -->   1  |      10
2  |       3         3  |       5
3  |       5         
```  
```
MAX(2)
```
```
t  |  one|  two         t  |  one|  two
---|-----|-----         ---|-----|-----
1  |   10|    1   -->   2  |   10|    4
2  |   10|    4         1  |   10|    1
3  |    5|    3         
```  


### Minimum (C,F)
If no number specified, Number will default to 1

``` sql
OPERATE (...) ... MIN(Number?)
```
```
MIN(2)
```
```
t  |  Signal         t  |  Signal
---|--------         ---|--------
1  |      10   -->   3  |       3
2  |       5         2  |       5
3  |       3         
```  
```
MIN(2)
```
```
t  |  one|  two         t  |  one|  two
---|-----|-----         ---|-----|-----
1  |   10|    1   -->   3  |    5|    3
2  |   10|    4         1  |   10|    1
3  |    5|    3         
```  

### Sort Signal (C,F)
Sorts the data in ascending order with the first column taking precedence, then the second, then ...

If Sort is specified with a 1 in the arguments it will sort in descending order

``` sql
OPERATE (...) ... SORT(1?)
```

### Sort Time (C,F)
Sorts time into ascending order

``` sql
OPERATE (...) ... SORTTIME()
```

### Get duplicates (C,F)
Removes values that do not occur more than once
``` sql
OPERATE (...) ... GETDUPLICATES()
```

### Remove duplicates (C,F)
removes values that occur more than once
``` sql
OPERATE (...) ... DROPDUPLICATES()
```

### Get above (C,F)
removes values that are not above specified value
``` sql
OPERATE (...) ... ABOVE(value)
```

### Get below (C,F)
removes values that are not below specified value
``` sql
OPERATE (...) ... BELOW(value)
```

### Mean (N,F)
Find the mean of each colunm and return this data
``` sql
OPERATE (...) ... MEAN()
```

### Median (N,F)
Finds the median for each column and return this data
``` sql
OPERATE (...) ... MEDIAN()
```

### Count (N,F)
Counts number of values in each column and returns this data
``` sql
OPERATE (...) ... COUNT()
```



