# Snapshot

This is the simplest of the operations. It is an easy way to view a snippet of the data you are creating.

The syntax is as follows,

```
SNAPSHOT (Name) Data_Name
```
For example

```
LOAD (Name) ... iwEngineSpeed ...

SNAPSHOT (Snap_1) Name
```
```
(In Output Terminal)

SNAPSHOT (Eng_Speed) 
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

[924 rows x 2 columns]

```