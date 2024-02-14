# Overview

Elphinstone Cloud Connect is an internal tool for taking advantage of vehicle data. It is capable of pooling data from multiple sources and of different data-types. The main use case for this software is to analyse historical canbus data from vehicles.

Making data

using a simple, and easy to use syntax. However, this does not limit Cloud Connect to simple operations; with **chaining** 

## Interface

## Input Files

## Config Files

## Steps

### What are Steps

*Steps* are the backbone of **Cloud Control**, they provide the functionality for simple queries, complex procedures and everything inbetween. Each line you write in the input file is considered a step, these can be chained together in any order to produce desired results.

### General syntax

Each step will always have these two features, a **TYPE** and a **(Name)**, what follows after is specific to each step type

```  sql
TYPE (Name) ...
```

### Types