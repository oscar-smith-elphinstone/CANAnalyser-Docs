# Operation

## Anatomy

## Functions

### Chainable

#### Add

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

#### Subtract

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

#### Multiply

The multiply function multiplies all values in table

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

#### Divide

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

//### Upsample
<!-- ### Downsample

Downsample will combine multiple data points together to acheive a desired time interval for the data. It takes two parameters
``` sql
OPERATION (...) ... DIVIDE(Value)
``` -->

#### Drop Null Values

``` sql
OPERATION (...) ... DROPNA()
```
```
DROPNA()
```
```
t  |  Signal         t  |  Signal
---|--------         ---|--------
1  |      10   -->   1  |      10
2  |     NaN         3  |       5
3  |       5           
```  

#### Rename Column
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

#### Maximum
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

#### Minimum
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

#### Sort signal

#### Sort time

#### Get duplicates

#### Remove duplicates

#### Get above

#### Get below





// ######################## non chainable
### Non-Chainable

#### Mean

#### Median

#### Count












#### Outliers
#### Rename
#### Drop Name

## Advanced

