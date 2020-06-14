# UiPathRPA-Extract-EmailAddress-Without-RegEx
Extract the email address from a string (without using RegEx)

Given a string containing one email address, create a workflow to extract the email address without using regular expressions.

Note: For input please use a String variable with the following value 
“Please use the following address to contact me john.doe@localcompany.com, it's the company email"

In UiPath Studio, create a new project and use the following steps:

  1.  Start the project as sequence and create 2 variables (a String and an Int32). Use 2 'Assign' activities - the first to 
      locate the "@" character, and the second to store its index (by using the 'IndexOf' method: 
      IndexTextToFind = VariableName.IndexOf("@")).
      
  2.  Extract all the text before and after "@" and store each in variables using 'Assign' activities, like EmailAddress_Part1 
      and EmailAddress_Part2.
      
  3.  Keep only the text portion from the last space character from EmailAddress_Part1 to the end and save it into the 
      EmailAddress_Part1variable, using the 'LastIndexOf' method in an 'Assign' activity: 
      EmailAddress_Part1.Substring(EmailAddress_Part1.LastIndexOf(" ")).
      
  4.  Extract all the text from EmailAddress_Part2 to the first space character (use an 'If' to check if the space exists; 
      if it doesn't, consider all the text as part of the email).
      
  5.  Print to output the email address using a 'Write Line' activity: i.e. "The email address is john.doe@localcompany.com."
  
