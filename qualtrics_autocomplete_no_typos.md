This code worked on Qualtrics in Semptember-October 2018. Qualtrics is notorious for making updates that break custom coding so keep in mind this may not work in the future. 

In studies that require participants to select from 100's of choices (such as social network nomination data) it is not feasible and highly inconvenient to make this question using a dropdown set of items on qualtrics because the drop down menu is not searchable.

The best solution in this case would be a text-box that participants can fill in and then have custom javascript code that shows pre-defined choices that the researchers want the participant to select from. 

The other important factors is that you want to reduce typos that are often caused by fill in the blank questions. So your javascript code will need to delete the whole text box if the partcipant type in exactly what the autocomplete code suggests. 

Then you make the question forced choice (or at least give them a warning if they try to progress without filling anything in). 

This is a tutorial for how to conveniently make the autocomplete code in Qualtrics

```
javascript code to be inserted into the questions 
```



talk about global vs local variable creation 
```
code to add to the h to make global variables 
```


