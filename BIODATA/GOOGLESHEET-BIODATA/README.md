
# GOOGLESHEET-ENABLED-HTML
HERE WE USE GOOGLE APP SCRIPT  TO STORE SUGGESTION FROM USER TO GOOGLE-SHEET

IN THE REPOSITORIES THERE ARE :

    1.index.HTML
    2.SUGGESTION.HTML
    3.SUGGESTION.CSS
    4.TEST.png
    5.BACKGROUNG.png
HERE index.HTML IS CONNECTED WITH BACKGROUNG.png (BACKGROUNG IMAGE) AND TEST.PNG (IMAGE OF A PERSON)

SUGGESTION.HTML AND SUGGESTION.CSS ARE CONNECTED TO EACH OTHER

INSIDE SUGGESTION.HTML WE HAVE USED  FETCH API METHOD TO POST FORM DATA
# SCRIPT USED IN .gs (GOOGLE APPS SCRIPT)


``` js
 
function doPost(e) {
  try {
    // Access the active spreadsheet
    const sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();

    // Define a new row array with form data
    const newRow = [
      e.parameters.fname[0],  // Accessing the value of the 'fname' parameter from the form submission
      e.parameters.mname[0],  // Accessing the value of the 'mname' parameter from the form submission
      e.parameters.lname[0],  // Accessing the value of the 'lname' parameter from the form submission
      e.parameters.email[0],  // Accessing the value of the 'email' parameter from the form submission
      e.parameters.phone[0],  // Accessing the value of the 'phone' parameter from the form submission
      e.parameters.SUGGESTION[0]  // Accessing the value of the 'SUGGESTION' parameter from the form submission
    ];

    // Append the new row to the spreadsheet
    sheet.appendRow(newRow);

    // Return a success message as plain text
    return ContentService.createTextOutput('Success').setMimeType(ContentService.MimeType.TEXT);
  } catch (error) {
    // If an error occurs during execution, return an error message
    return ContentService.createTextOutput('Error: ' + error.message).setMimeType(ContentService.MimeType.TEXT);
  }
}


```
    

# IN HTML FILE



``` HTML
<script>
    const scriptURL = 'ENTER YOUR DEPLOYED SCRIPT URL'; // Variable storing the URL to submit the form data
    const form = document.forms['submit-to-google-sheet']; // Get the form by name attribute

    function submitForm() {
        fetch(scriptURL, { method: 'POST', body: new FormData(form) }) // Use Fetch API to post form data
        .then(response => {
            console.log('Response:', response); // Log the response
            if (!response.ok) {
                throw new Error('Network response was not ok'); // Throw error if response is not ok
            }
            return response.text(); // Return response text
        })
        .then(data => {
            console.log('Success!', data); // Log success message with data
            form.reset(); // Reset the form after successful submission
        })
        .catch(error => {
            console.error('Error!', error); // Log error if fetch fails
        });
    }

</script> 
```
#### THE OUTPUT OF THE JAVASCRIPT WILL BE SHOWN AT CONSOLE OF THE BROWSER





# TABLE MUST CONTAIN

#### FOLLOWING THINGS



| FIRST NAME | MIDDLE NAME     |LAST NAME                | 
| :-------- | :------- | :------------------------- |
| DATA |DATA  |DATA  |

| EMAIL ID | PHONE NUMBER     |SUGGESTION                |
| :-------- | :------- | :------------------------- |
|DATA  | DATA | DATA |

#### NOTE THE TABLE HEADING MUST BE IN SINGLE ROW 


## TAKEN HELP FROM : YOUTUBE, CHAT-GPT 3.5



