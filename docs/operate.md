# Operate

The operate step is the most powerful but also the hardest step to learn. It lets you take any data and perform a series of sequential operations on it. These operations are simple but when combined together can acheive complex behaviour.

Most operations can be performed on single and multicolumn data but some operations only work on single column data. Some operate functions are also denoted as **finishing** this is because the data they output cannot be operated on and can only be used in steps such as Snapshot and Export.

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


### Flexible (F)
These functions work with both single and multicolumn data

### Single Column (S)
These functions will only work if the data input has a single column, therefore these functions will not work with data from a TABLE operation.


## Functions
The functions execute sequentially from left to right, each has a name identifier and an argument input


### Add (C,S)

The add function adds any number to all values in a table

``` sql
OPERATION (...) ... ADD(Value)
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
OPERATION (...) ... SUBTRACT(Value)
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
OPERATION (...) ... MULTIPLY(Value)
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
OPERATION (...) ... DIVIDE(Value)
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
OPERATION (...) ... RENAME(Name)
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



### Remove Gaps (C,F)

``` sql
OPERATION (...) ... DROPGAP()
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
OPERATION (...) ... FILLGAP(value)
```

### Forward Fill Gaps (C,F)
Fills gaps with previously found data, will fill an unlimited amount of gaps after a data point. If specified can limit the fill reach
``` sql
OPERATION (...) ... FFILL(number?)
```

### Back Fill Gaps (C,F)
Fills gaps with values ahead if found, will fill an unlimited amount of gaps before a data point. If specified can limit the fill reach
``` sql
OPERATION (...) ... BFILL(number?)
```

### Interpolate (C,F)
Fills gaps using linear interpolation between existing data points and gaps
``` sql
OPERATION (...) ... INTERPOLATE(number?)
```

### Maximum (C,F)
If no number specified, Number will default to 1

``` sql
OPERATION (...) ... MAX(Number?)
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
OPERATION (...) ... MIN(Number?)
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
OPERATION (...) ... SORT(1?)
```

### Sort Time (C,F)
Sorts time into ascending order

``` sql
OPERATION (...) ... SORTTIME()
```

##### Get duplicates

##### Remove duplicates

##### Get above

##### Get below

#### Multiple Column
These are functions which only work on table, no functions are currently covered by this description\

#### Mean

#### Median

#### Count

#### Outliers
#### Rename
#### Drop Name

## Advanced

