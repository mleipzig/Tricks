edits to be made 

1. finish local vs global variable creation 



This code worked on Qualtrics in Semptember-October 2018 and again in December 2018. Qualtrics is notorious for making updates that break custom coding so keep in mind this may not work in the future. 

<strong> Somehow only one form field out of more than 100k+ different form fields had a typo in their response so the code may not be full proof, but I cannot determine how that single form field had a typo (the name was off by one character even though it was correctly spelled in the code). </strong> Regardless, I still believe this code is very convenient. 

In studies that require participants to select from 100's of choices (such as who to nominate in their dorm for "most liked" person) it is not feasible and highly inconvenient to use the normal dropdown question types provided by Qualtrics because the drop down menu is not searchable. I can't type in "t" and see all the options that start with "t" in them. 

The best solution in this case would be a text-box that participants can fill in and then have custom javascript code that shows pre-defined choices that the researchers want the participant to select from. 

Another important factor is that you want to reduce typos that are common with fill in the blank questions. So your javascript code will need to delete the whole text box if the partcipant type in exactly what the autocomplete code suggests. 

Then you make the question forced choice (or at least give them a warning if they try to progress without filling anything in). This means you will receive no typos. 

This is a tutorial for how to conveniently make the autocomplete code in Qualtrics. 
Please note that some Qualtrics survey templates do not work with this code or are horribly formatted. No idea why. I got this to work with the "modern" template.


First in order to make javascript a viable option in your survey you must edit the "header" of the survey. To do this go to 
"Look and Feel". Select "edit" underneath the "Header" bar. In the textbox that appears click the "source" button (the one that looks like a page with <> on it). Now add this code. 


```
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"></script>
<link href="https://ajax.googleapis.com/ajax/libs/jqueryui/1.8/themes/base/jquery-ui.css" rel="stylesheet" /><script src="https://ajax.googleapis.com/ajax/libs/jqueryui/1.8/jquery-ui.min.js"></script>
```

Great! Now you can put in the auto-complete code. 

Click on the wheel next to the question you want to add the autocomplete code to. 

Select "add javascript". You'll get a window with this code in it 

```
Qualtrics.SurveyEngine.addOnload(function()
{
	/*Place your JavaScript here to run when the page loads*/

});

Qualtrics.SurveyEngine.addOnReady(function()
{
	/*Place your JavaScript here to run when the page is fully displayed*/

});

Qualtrics.SurveyEngine.addOnUnload(function()
{
	/*Place your JavaScript here to run when the page is unloaded*/

});


```

You'll want to add this code to the addOnReady function part

```
	var list =  ['insert', 'different', 'strings', 'like', 'this']

var source = list;
	jQuery("#"+this.questionId+" .InputText").autocomplete({
        minLength: 0,
        source: source,
        autoFocus: true,
        scroll: true,
    }).focus(function() {
        $(this).autocomplete("search", "");
    }).on("blur", function(event) {
		var autocomplete = $(this).data("autocomplete");
        var matcher = new RegExp("^" + $.ui.autocomplete.escapeRegex($(this).val()) + "$", "i");
        autocomplete.widget().children(".ui-menu-item").each(function() 
          {
            var item = $(this).data("item.autocomplete");
            if (matcher.test(item.label || item.value || item)) {
                autocomplete.selectedItem = item;
                return;
            }
        });

        if (autocomplete.selectedItem) {
            autocomplete._trigger("select", event, {
                item: autocomplete.selectedItem
            });
        } else {
            $(this).val('');
        }	
});

```
If you would like to individualize the form fields so some form fields show certain answers than the other form fields you can choose specific form field IDs by replacing the code on line 72 
`jQuery("#"+this.questionId+" .InputText").autocomplete({`

with this 
`jQuery("[id='QR~QID1~1']")`
with the `~1` referring to the form field ID you wish to reference. The form fields are <b>usually</b> ordered from 1 to how many form fields you have, but that's not always the case. You can check what the form field IDs are by exporting the data dictionary with instructions found <a href="https://www.qualtrics.com/community/discussion/1062/generate-survey-data-dictionary-and-export-to-word">here</a>
 

Note what happens if you have names with ' in the `var list` like `O'Reily`. In these cases the autocomplete won't work so you must eliminate ' from your lists. Make sure to note this choice if you make a key for your names and want to de-identify them. 
 
Also, in case you were wondering, you can make this list `var list =  ['insert', 'different', 'strings', 'like', 'this']
` 
vertical like this 
```
var list =  [
'insert', 
'different', 
'strings', 
'like', 
'this']
```


will talk about global vs local variable creation in Qualtrics in the future 
```
code to add to the h to make global variables 
```


