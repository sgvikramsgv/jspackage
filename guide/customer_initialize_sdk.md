{{= BackToPackageOverview }}

#Initializing the Customer Service

This article discusses how to initialize the Customer service within your website.

##Creating a Client

The central class of the Sharing Services Package is {{=C_windowAvayaCoBrowseClientServices}}. Customer website using the Sharing Services Package has its own instance of {{=C_windowAvayaCoBrowseClientServices}} and maintains a reference to this object in order to start an {{=C_ServicesCobrowseCustomerCustomerCobrowse}} and access features within the SDK.

##Client Configuration

As part of the process to create your client instance, you must create a {{=C_ConfigCoBrowseConfiguration}} object that defines your website. The attributes you define within {{=C_ConfigCoBrowseConfiguration}} will be used to interact with Breeze server over the network:

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

Note: For more information on service configuration, see <a href=../guide/configuring_the_sdk.gsp">Configuring the SDK</a>.

##Creation of the Client object

Create a {{=C_windowAvayaCoBrowseClientServices}} instance

```javascript
    var _coBrowseAgentClientService = new AvayaCoBrowseClientServices(_cbconfig);
	// To register logger
    _coBrowseAgentClientService.registerLogger(window.console);
```

##Start Customer Service

Start the agent service

```javascript
	_cbinstance = _coBrowseAgentClientService.createCustomerCobrowse(_cbconfig);
    _cbinstance.start();
```
##Register Callbacks

Callbacks are used to handle events that occur during the active Co-Browsing session.

##Register OnConnectionReset Callback

addOnConnectionResetCallback is called to report that the network connection has been re-established. 

```javascript
    _cbinstance.addOnConnectionResetCallback(function (evt) {
		// Called to report the network connection has been 
		// re-established
		// Add code here to notify customer
    });
```

##Register OnConnectionFailure Callback

addOnConnectionFailureCallback is called to report that the network connection is failed. 

```javascript
    _cbinstance.addOnConnectionFailureCallback(function (evt) {
        // Called to report the network connection is 
		// failed
		// Add code here to notify customer
    });
```

##Register OnConnection Callback

addOnConnectionCallback is called to report that the network connection has been established. 

```javascript
   _cbinstance.addOnConnectionCallback(function (evt) {
        // Called to report the network connection has been 
		// established
		// Add code here to notify customer
    });
```

##Register OnSessionClose Callback

addOnSessionCloseCallback is called to report that the Agent has closed Co-Browsing session. 

```javascript
    _cbinstance.addOnSessionCloseCallback(function (evt) {
        // Called to report the agent has 
		// closed co-browsing session
		// Add code here to notify customer
    });
```

##Register OnControlRequest Callback

addOnControlRequestCallback is called to report that the Agent has requested Co-Browsing session control. 

```javascript
    _cbinstance.addOnControlRequestCallback(function (evt) {
        // Called to report the agent has 
		// requested co-browsing session control
		// Add code here to notify customer
    });
```

##Register OnControlRelease Callback

addOnControlReleaseCallback is called to report that the Agent has released Co-Browsing session control. 

```javascript
    _cbinstance.addOnControlReleaseCallback(function (evt) {
        // Called to report the agent has 
		// released co-browsing session control
		// Add code here to notify customer
    });
```

##Register OnfireInactivity Callback

addOnfireInactivityCallback is called to report that the Customer is inactive during active Co-Browsing session. 

```javascript
    _cbinstance.addOnfireInactivityCallback(function (msg) {
        // Called to report the customer is inactive during 
		// active co-browsing session
		// Add code here to notify customer
    });
```

##Register OnStopInactivity Callback

addOnStopInactivityTimerCallback is called to report that the Customer is active during active Co-Browsing session. 

```javascript
    _cbinstance.addOnStopInactivityTimerCallback(function (msg) {
        // Called to report the customer is active during 
		// active co-browsing session
		// Add code here to notify customer
    });
```

##Register OnAgentJoin Callback

addOnAgentJoinCallback is called to report that the Agent has joined Co-Browsing session control. 

```javascript
    _cbinstance.addOnAgentJoinCallback(function (evt) {
        // Called to report the agent has 
		// joined co-browsing session control
		// Add code here to notify customer
    });
```

##Reinitializing a Service

Support to reinitialize Customer service feature is planned for the future release.
