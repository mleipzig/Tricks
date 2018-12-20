Scoring data composites 
Reverse scoring 
Handeling missing data
Basic statistical tests and the math behind them

A demonstration of constructing a composite score of the mean of multiple columns based on column name

```
df=data.frame("column1"=1:5, "column2"=2:6, "column3"=3:7) #this creates a dataframe for you so you can look at the data 
df$newColumn=rowMeans(df[c("column1","column2","column3")]) #this creates the new column that contains your composite scores. In this case you calculated the mean hence the "rowMeans" command. If you want the sum you should do "rowSums". 
```
