{{= BackToPackageOverview }}

#Initializing the Agent Service

This article discusses how to initialize the Agent Service within your website.

##Creating a Client

The central class of the Co-Browsing Services is {{=C_windowAvayaCoBrowseClientServices}}. Agent website using the Client SDK has its own instance of {{=C_windowAvayaCoBrowseClientServices}} and maintains a reference to this object in order to start an {{=C_ServicesCobrowseAgentAgentCobrowse}} and access features within the SDK.

##Client Configuration

As part of the process to create your client instance, you must create a {{=C_ConfigCoBrowseConfiguration}} object that defines your website. The attributes that you define within {{=C_ConfigCoBrowseConfiguration}} are used to interact with Breeze server over the network:

```javascript
    _cbconfig = new AvayaCoBrowseClientServices.Config.CoBrowseConfiguration();
	
	//Set FQDN/hostname of the breeze server
    _cbconfig.serverInfo.hostName = "localhost";
	
	//Set the port number to access breeze server 
    _cbconfig.serverInfo.port = '8443';
	
	//Set to true for secure communication. Default value is false 
    _cbconfig.serverInfo.isSecure = true;
	
	//To enable co-browsing.Default value is false
    _cbconfig.enabled = true;
```

Note: For more information on service configuration, see <a href="../guide/configuring_the_sdk.gsp">Configuring the SDK</a>.</p>

##Creation of the Client object

Create an {{=C_windowAvayaCoBrowseClientServices}} instance.

```javascript
    var _coBrowseAgentClientService = new AvayaCoBrowseClientServices(_cbconfig);
	
	// To register logger
    _coBrowseAgentClientService.registerLogger(window.console);
```

##Start Agent Service

Start the Agent service.

```javascript
	_cbinstance = _coBrowseAgentClientService.createAgentCobrowse(_cbconfig);
	
	// To set IFrame which renders customer webpage
    _cbinstance.setIFrame(_iframeId);
    _cbinstance.start();
```

##Register Callbacks

Callbacks are used to handle events that occur during an active Co-Browsing session.

##Register OnPause Callback

addOnPauseCallback is called to report that the Customer has paused the Co-Browsing session. 

```javascript
    _cbinstance.addOnPauseCallback(function () {
		// Called to report the customer has 
		// paused co-browsing session
		// Add code here to notify agent
    });
```

##Register OnResume Callback

addOnResumeCallback is called to report that the Customer has resume the Co-Browsing session. 

```javascript
    _cbinstance.addOnResumeCallback(function () {
        // Called to report the customer has 
		// resume co-browsing session
		// Add code here to notify agent
    });
```

##Register OnControlGrant Callback

addOnControlGrantCallback is called to report that the Customer has granted the Co-Browsing session control. 

```javascript
    _cbinstance.addOnControlGrantCallback(function () {
        // Called to report the customer has 
		// granted co-browsing session control
		// Add code here to notify agent
    });
```

##Register OnControlDenial Callback

addOnControlDenialCallback is called to report that the Customer has denied the Co-Browsing session control. 

```javascript
    _cbinstance.addOnControlDenialCallback(function () {
        // Called to report the customer has 
		// denied co-browsing session control
		// Add code here to notify agent
    });
```

##Register OnControlRevoke Callback

addOnControlRevokeCallback is called to report that the Customer has revoked the Co-Browsing session control. 

```javascript
    _cbinstance.addOnControlRevokeCallback(function () {
        // Called to report the customer has 
		// revoked co-browsing session control
		// Add code here to notify agent
    });
```

##Register OnSessionClose Callback

addOnSessionCloseCallback is called to report that the Customer has closed the Co-Browsing session control. 

```javascript
    _cbinstance.addOnSessionCloseCallback(function (evt) {
        // Called to report the customer has 
		// closed co-browsing session control
		// Add code here to notify agent
    });
```

##Register OnCustomerJoin Callback

addOnCustomerJoinCallback is called to report that the Customer has joined the Co-Browsing session. 

```javascript
    _cbinstance.addOnCustomerJoinCallback(function () {
        // Called to report the customer has 
		// joined co-browsing session control
		// Add code here to notify agent
    });
```

##Register OnConnectionFailure Callback

addOnConnectionFailureCallback is called to report that the network connection is failed. 

```javascript

    _cbinstance.addOnConnectionFailureCallback(function (evt) {
        // Called to report the network connection is 
		// failed
		// Add code here to notify agent
    });
```

##Register OnConnection Callback

addOnConnectionCallback is called to report that the network connection is established. 

```javascript
    _cbinstance.addOnConnectionCallback(function (evt) {
        // Called to report the network connection has been 
		// established
		// Add code here to notify agent
    });
```

##Register OnInActivityTimeOutOccurred Callback

addOnInActivityTimeOutOccurredCallback is called to report that the Agent is inactive during an active Co-Browsing session. 

```javascript
    _cbinstance.addOnInActivityTimeOutOccurredCallback(function (message) {
        // Called to report the agent is inactive during 
		// active co-browsing session
		// Add code here to notify agent
    });
```

##Register OnStopInActivityTime Callback

addOnStopInActivityTimeOutCallback is called to report that the Agent has become active during an active Co-Browsing session. 

```javascript   
    _cbinstance.addOnStopInActivityTimeOutCallback(function (message) {
        // Called to report the agent has become active during 
		// active co-browsing session
		// Add code here to notify agent
    });
```

##Reinitializing a Service

Support to reinitialize Agent service feature is planned for the future release.