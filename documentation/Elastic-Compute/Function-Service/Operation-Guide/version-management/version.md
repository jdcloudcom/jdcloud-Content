# Version
With version management, you can release multiple versions of functions to serve different environments and implement iteration and upgrade of each environment version. The default version of Function Creation is LATEST version, and each function has a LATEST version. When the function code is stable, release operation can be done, changes of the release revision are not allowed.

Suggestion: You can use the function version service for on-line requests that is released after tested stable, and continue to develop tests on the LATEST version to ensure smooth running of the business.

## Release Version

 1. The user logs in Function Service, go to the "Function List" page.
 
 2. Select the function to be configured in "Function List", click the function name to enter the function details.
 
 3. Select the LATEST version on the function details, click "Operation"-"Release New Version", pop up "Release New Version" window.
 
 4. Enter configuration information (see Table 1) of the function version to be released on the "Release New Version" interface.
 
 5. Click "Release"，complete version creation.
 
 Table 1: Function Version Configuration Information Table

| Configuration Information | Description                                                       |
| -------- | ---------------------------------------------------------- |
| Description     | A maximum of 1,000 English letters, digits, spaces, commas, English full stops and Chinese characters are supported. |



 **Note:**

Version number is automatically generated by the system (use date and time as version number, for example: v20180819-190658).

A maximum of 10 versions can be released under single function.

A new version of function can be released until its configuration or code is changed.


## Delete Version

On the function details, select the function version, click "Operation" - "Delete Version", and pop up "Delete Notification", Click "OK" to delete the function version.

 
