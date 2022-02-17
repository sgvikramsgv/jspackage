{{= BackToPackageOverview }}

#Configuring the Sample App for Sharing Services Package

Before using the features in the Sample App, you must acquire configuration information from your administrator to allow the Sample App to connect to required network services.


##Service Configuration Worksheet

The section helps you to identify the services that you will be using. This section also helps you to identify the corresponding configuration information you must request. 

### Agent Service {{=C_ServicesCobrowseAgentAgentCobrowse}}

* Configuration Object {{=C_ConfigCoBrowseConfiguration}}  

### Customer Service {{=C_ServicesCobrowseCustomerCustomerCobrowse}}

* Configuration Object {{=C_ConfigCoBrowseConfiguration}} 

#### Information to request from your administrator for Agent Service and Customer Service

* Network&nbsp;Parameters: Breeze IP/FQDN, port, TLS on/off
* Certificate for TLS connections to Breeze

##Configure the Co-browsing sample Customer website

+ Locate cobrowse_test_app application on the tomcat server
+ Open the following file in a text editor or JavaScript editor, and modify the host information for the Customer:
cobrowse_test_app/cobrowse/customer/js/app.js

The following is an example of the modified information:

``` javascript

//FQDN/hostname of the breeze server
_cbconfig.serverInfo.hostName = "";

//set the port number to access breeze server 
_cbconfig.serverInfo.port = '';

//set to true for secure communication. Default value is false 
_cbconfig.serverInfo.isSecure = true;
```

+ To access the sample Customer website, open the  <https://FQDN/ServerIP:port/cobrowse_test_app/cobrowse/customer/index.html>

##Configure the Co-browsing sample Agent website

+ Locate cobrowse_test_app application on tomcat server
+ Open the following file in a text editor or JavaScript editor, and modify the host information for the Agent:
cobrowse_test_app/cobrowse/agent/js/app.js

The following is an example of the modified information:

``` javascript
//FQDN/hostname of the breeze server
_cbconfig.serverInfo.hostName = "";

//set the port number to access breeze server 
_cbconfig.serverInfo.port = '';

//set to true for secure communication. Default value is false 
_cbconfig.serverInfo.isSecure = true;
```

+ To access the sample Agent website, open the  <https://FQDN/ServerIP:port/cobrowse_test_app/cobrowse/agent/index.html>


##Configure the Co-browsing sample Admin Website

+ Locate cobrowse_test_app application on tomcat server
+ Open the following file in a text editor or JavaScript editor, and modify the host information for the Admin :
cobrowse_test_app/cobrowse/admin/js/app.js

The following is an example of the modified information:

``` javascript
//"<FQDN/Hostname> is FQDN/hostname of the breeze server and <port> is the port number to access the breeze server
var serverURL = 'https:// "<FQDN/Hostname>:<port>/services/CoBrowse';
```

+ To access the sample Admin website, open the  <https://FQDN/ServerIP:port/cobrowse_test_app/cobrowse/admin/index.html>

<p class="av-note"><span>Note:</span>Co-Browsing snap-in provides ReST APIs to audit Co-Browsing session information.
Sample admin website is built using audit Rest APIs. Sample admin website does not use Co-Browsing JavaScript SDK.
</p>

