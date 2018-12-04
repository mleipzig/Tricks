Tested on Mac only

Issues to fix 
<b> 1. Need to add upated version that will deface and then replace with the BIDS validated filename in it </b>


This is a short tutorial for automatically defacing data in a BIDS validated directory using mri_deface. 
I'd like to move to pydeface, but I'm having some errors with it so I'll stick with mri_deface for now

To download mri_deface go here https://surfer.nmr.mgh.harvard.edu/fswiki/mri_deface
mri_deface does not require a Freesurfer license. 

Download the correct mri_deface file based on your operating system which you can discern from the file name. Also, download these two files 
1. talairach_mixed_with_skull.gca 
2. face.gca 

Once you've downloaded these 3 files you can follow the documentation. However, be aware that there is an incorrect line in the mri_deface dcoumentation. In the documentation you'll see these set of instructions. 

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
you should copy (cp) the UNZIPPED file like this 

```
cp mri_deface-v1.22-Linux64 mri_deface
```


Then proceed with the other steps which are 

```
chmod a+x mri_deface
gunzip talairach_mixed_with_skull.gca.gz
gunzip face.gca.gz

```


Okay so back to business. 
Use the find command like so 

```


find insert/path/of/BIDS/directory  -path "*anat*/*.nii.gz*" -execdir /your/mri_deface/path {} /path/to/talairach_mixed_with_skull.gca /path/to/face.gca  my_T1_defaced.nii \;


```

and now the jobs will be automated for you. De-facing takes about 5 minutes per T1.   
One downside of this script is you lose the BIDS valid file format name and your T1's will all be named `my_T1_defaced.nii`. <b> I'll update some point in the future with code to fix that </b>



If you do not have a BIDS valid dataset just replace the `anat` part in 

```
-path "*anat*/*.nii.gz*"
```

to include whatever keyword in your folder/directory indicates there are ONLY T1 files inside that directory. If you keep your T1 and T2* (T2* aka BOLD or functional MRI) nifti files in the same folder I'm 99% certain this code will NOT work and will throw an error and not deface anything because mri_deface throws an error when you try to run it on BOLD files 


You should also always check that the T1 was defaced without losing any of the brain.
