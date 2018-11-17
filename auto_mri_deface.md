Tested on Mac only

This is a short tutorial for automatically defacing data in a BIDS validated directory using mri_deface. 
I'd like to move to pydeface, but I'm having some errors with it so I'll stick with mri_deface for now

mri_deface can be found here https://surfer.nmr.mgh.harvard.edu/fswiki/mri_deface
It does not require a license. 

There is an incorrect line in the mri_deface dcoumentation above. In the documentation you'll see these set of instructions. 


```
gunzip mri_deface-v1.22-Linux64.gz
cp mri_deface-v1.22-Linux64.gz mri_deface
chmod a+x mri_deface
gunzip talairach_mixed_with_skull.gca.gz
gunzip face.gca.gz

```

The second line is incorrect and instead of 

```
cp mri_deface-v1.22-Linux64.gz mri_deface

```
you should copy the UNZIPPED file like this 

```
cp mri_deface-v1.22-Linux64 mri_deface
```


Then proceed with the other steps



Okay so back to business. 
Just use the find command like so 

```


find insert/path/of/BIDS/data  -path "*anat*/*.nii.gz*" -execdir /your/mri_deface/path {} /path/to/talairach_mixed_with_skull.gca /path/to/face.gca  my_T1_defaced.nii \;


```

and now the jobs will be automated for you. De-facing takes about 5 minutes per T1.  
One downside of this script is you lose the BIDS valid file format name. I'll update some point in the future with code to fix that



If you do not have a BIDS valid dataset just replace the `anat` part in 

```
-path "*anat*/*.nii.gz*"
```

to include whatever keyword in your folder/directory indicates there are ONLY T1 files inside. If you keep your T1 and T2* nifti files in the same folder this code will probably NOT work
