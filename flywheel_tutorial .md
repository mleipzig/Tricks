This is a tutorial to use flywheel based on my experience at the CNI at Stanford. This has been validated on Mac OS as of November 2018. 
Flywheel is a great resource, but still nascent. A lot of changes are being amde to it so this tutorial may become defunct over time. 
Also, note that I'll be borrowing a lot of material from the current flywheel documentation and adding my own comments to it. 

<h3> Flywheel on your web broswer </h3>

Actual documentation for the web browser is pretty well supported so will just link the current flywheel documentation for that here 
https://docs.flywheel.io/display/EM/Managing+Data





<h3> Logging into flywheel through your terminal </h3> 

First follow these instructions to install the flywheel CLI (command line interface) 
https://docs.flywheel.io/display/EM/CLI+-+Installation






<h3> Getting data into BIDS format </h3>


<b> Talk about BIDS format and purpose </b>


<b> Comment on possible issue with the "download" command and how you need to use export. </b>

<b> way to make sure you only have to use "fw" command instead of full file path of "fw" </b>


In order for the export command to work on a full project, every single file must be BIDS validated. 
The error message you get when you try to download a project with some files that are not BIDS valid does not explicitly state this, but this is what happened to me. 
When you try to run export command you may notice that you'll see a message that looks like 

<b> insert error message </b>

You must either fix the files and make them BIDS valid or move all of these files to a different project. 


Talk about how to make files BIDS valid 








