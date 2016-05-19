# MAPI and FSSHTTPWOPI Inspectors for Fiddler
This tutorial shows you how to install MAPI and FSSHTTPandWOPI Inspectors for Fiddler.

The Messaging Application Programming Interface (MAPI) Inspector for [Fiddler](http://www.telerik.com/fiddler) decodes the MAPI message payload of an HTTP POST request and response according to [MS-OXCMAPIHTTP](https://msdn.microsoft.com/en-us/library/Dn530952(v=EXCHG.80).aspx). The MAPI Inspector is displayed under the *Inspectors* tab in Fiddler.

In addition to the MAPI Inspector, the File Synchronization via SOAP over HTTP Protocol (FSSHTTP) and the Web Application Open Platform Interface Protocol (WOPI)�combined as FSSHTTPandWOPI�also has a plug-in inspector for Fiddler which decodes:
* FSSHTTP protocol message that enables one or more clients to synchronize changes done on shared files stored on a server.
* WOPI protocol message that enables a client to access and change files stored by a server. 

The FSSHTTPandWOPI Inspector is displayed under the *Inspectors* tab in Fiddler and decodes the message payload according to [MS-FSSHTTP](https://msdn.microsoft.com/en-us/library/dd943623%28v=office.12%29.aspx), [MS-FSSHTTPB](https://msdn.microsoft.com/en-us/library/dd965780%28v=office.12%29.aspx), [MS-FSSHTTPD](https://msdn.microsoft.com/en-us/library/ee365790%28v=office.12%29.aspx) and [MS-WOPI](https://msdn.microsoft.com/en-us/library/hh622722%28v=office.12%29.aspx).

This repository also includes Jscript that adds an *MS Protocol* column in the Fiddler web session panel. The *MS Protocol* column displays protocols that are relevant to MAPI, FSSHTTP, and WOPI messages, thereby allowing you to easily identify which HTTP requests and responses contain the respective message payloads.

This README document provides the instruction on installing one or both inspectors. 

For details on how to use the inspectors: see [*MAPI Inspector for Fiddler User Guide*](https://github.com/OfficeDev/MAPI-Inspector-for-Fiddler/wiki), see also FSSHTTPandWOPI Inspector for Fiddler User Guide.

## Installation 
First install the latest [Fiddler](http://www.telerik.com/fiddler) tool and then run it. Note that Fiddler must be run at least once before installing any inspectors. To install the inspector of your choice (MAPI, FSSHTTPWOPI) or to install both, add the respective DLL files and the scripts.

###Inspector DLL###
1. Copy the file MAPIFiddlerInspector.dll into the C:\Program Files\Fiddler2\Inspectors directory. Alternatively, you can clone this repository, build the MAPIFiddlerInspector.dll, and copy the built .dll to your C:\Program Files\Fiddler2\Inspectors directory.

   Follow the same process if you wish to use FSSHTTPAndWOPIFiddlerInspector.dll.

2. Restart Fiddler. MAPI, FSSHTTPandWOPI or both Inspectors will appear under the *Inspectors* tab for request and response. See the following screenshot.

    ![alt tag](/README-Images/InspectorsTabs.png)

###Script ###

1. From the *Rules* menu, which is shown in the following screenshot, click *Customize Rules*.
    
    ![alt tag](/README-Images/Figure2-mapiscript.png)

2. When the following message box displays, click *Yes* to install the FiddlerScript editor.

    ![alt tag](/README-Images/Figure3-mapiscript.png)

3. Restart Fiddler after installing the FiddlerScript editor. Fiddler displays a new tab, *FiddlerScript*, as shown in the following screenshot. 

    ![alt tag](/README-Images/Figure4-mapiscript.png)

4. Copy the code from the MAPI.js file and paste it into the definition for the **Handlers** class. Click *Save Script* to save the script. Follow the same process if you wish to use only the FSSHTTPAndWOPI.js file.

   But if you wish to add the code from the FSSHTTPAndWOPI.js file, then update **CalcMethodCol** function definition with the code for FSSHTTP and WOPI. Don't forget to add **GetWOPIOperationName** function definition as well.

   **Note:** When you combine the scripts for MAPI and FSSHTTP in function **CalcMethodCol**, modify the code accordingly to ensure protocol names are displayed under the *MS Protocol* column. As shown below, the else statement is removed and the if statement for MAPI is added.
   
   ![alt tag](/README-Images/ScriptMAPIAndFSSHTTP.png)

5. Restart Fiddler. The *MS Protocol* column is displayed in the session view.


    ![alt tag](/README-Images/Figure5-mapiscript.png)

