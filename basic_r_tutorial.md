Scoring data composites 
Reverse scoring 
Handeling missing data

A demonstration of constructing a composite of the mean of multiple columns 

```
df=data.frame("column1"=1:5, "column2"=2:6, "column3"=3:7) #this creates a dataframe for you
df$newColumn=rowMeans(df[c("column1","column2","column3")]) #this creates the new column 
```
