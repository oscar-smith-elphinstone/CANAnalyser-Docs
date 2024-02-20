# Load

The Load step is the most imporant of all the steps. It is responsible for retrieving data from the various data sources and making it available to any steps that follow. However, it is also one of the easiest steps to learn.

``` sql
LOAD (Name) source device signal <date from> <date to>
```
Example
``` sql
LOAD   (Eng_Speed)  s3  2A711C91 iwEngineSpeed  <18/01/24,04:00:00>  <18/01/24,04:04:05>
```
```
                             t  iwEngineSpeed
0   2024-01-18 04:00:00.062800         1982.0
1   2024-01-18 04:00:00.322650         1982.0
2   2024-01-18 04:00:00.582000         1983.0
3   2024-01-18 04:00:00.842500         1981.0
4   2024-01-18 04:00:01.102850         1980.0
..                         ...            ...
919 2024-01-18 04:03:58.701900          781.0
920 2024-01-18 04:03:58.964000          864.0
921 2024-01-18 04:03:59.221350         1110.0
922 2024-01-18 04:03:59.484850         1292.0
923 2024-01-18 04:03:59.740400         1495.0
```