
Update with how to make this automated using the find command 


Assuming that you've performed the 1st level analyses in FSL


First, go to the path you specified as your output directory and find your feat directory.

Inside the feat directory go to the “reg” directory. 

Delete all the .mat files inside the “reg” directory using this command 
```
rm *.mat  
```
Next run this command 

```
cp $FSLDIR/etc/flirtsch/ident.mat reg/example_func2standard.mat
```
 
Then run this command to overwrite the standard.nii file with the mean_func.nii.gz file (the mean_func.nii file is located in the feat directory and not  

 ```
cp mean_func.nii.gz reg/standard.nii.gz
```
