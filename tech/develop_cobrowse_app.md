{{= BackToPackageOverview }}

#Developing Co-Browsing Websites

The Sharing Services Package provides application developers a simple, easy-to-use APIs to enable Co-Browsing feature in
Agent and Customer website. This article describes implementation of Co-Browsing features in agent and Customer website.

## Co-browsing features 

* Agent or Customer Initiated Co-Browsing session
* Pause/Resume
* Agent/Customer in control
* Agent Synchronization
* Inactivity/session timeout
* Hovering and Highlight Text
* Secure fields masking and disable submit button 
* Alerts, if participants disconnected

Note: Detailed information about Co-Browsing features is avaialable in Avaya Co-Browsing Snap-in Reference guide. 
Read documentation section in <a href="../tech/gettingstarted.gsp">Getting Started</a>.
</p>

### Agent Initiated Co-Browsing session

This section describes 

* <a href="../guide/agent_initialize_sdk.gsp">Initializing the Agent Service</a>
* <a href="../guide/customer_initialize_sdk.gsp">Initializing the Customer Service</a>
* <a href="../guide/agent_request_session.gsp">Request Co-Browsing Session</a>
* <a href="../guide/customer_live_join_session.gsp">Join Co-Browsing Session</a>
* <a href="../guide/customer_pause_session.gsp">Pause Co-Browsing Session</a>
* <a href="../guide/customer_resume_session.gsp">Resume Co-Browsing Session</a>
* <a href="../guide/agent_request_control.gsp">Request Co-Browsing Session Control</a>
* <a href="../guide/customer_deny_control.gsp">Deny Co-Browsing Session Control</a>
* <a href="../guide/customer_deny_control.gsp">Grant Co-Browsing Session Control</a>
* <a href="../guide/agent_release_control.gsp">Release Co-Browsing Session Control</a>
* <a href="../guide/customer_logout_session.gsp">Logout Co-Browsing Session</a>

![Overview]({{=BpImages}}javascript/sharing/tech/AgentInitiatedSession.png)

#### Agent Website

This describes implementation of Agent Service Co-Browsing features on Agent Website

##### Agent Service Initialization

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

    var _coBrowseAgentClientService = new AvayaCoBrowseClientServices(_cbconfig);
	// To register logger
    _coBrowseAgentClientService.registerLogger(window.console);

	_cbinstance = _coBrowseAgentClientService.createAgentCobrowse(_cbconfig);
	// To set IFrame which renders customer webpage
    _cbinstance.setIFrame(_iframeId);
    _cbinstance.start();

    _cbinstance.addOnPauseCallback(function () {
		// Called to report the customer has 
		// paused co-browsing session
		// Add code here to notify agent
    });
	
    _cbinstance.addOnResumeCallback(function () {
        // Called to report the customer has 
		// resume co-browsing session
		// Add code here to notify agent
    });

    _cbinstance.addOnControlGrantCallback(function () {
        // Called to report the customer has 
		// granted co-browsing session control
		// Add code here to notify agent
    });

    _cbinstance.addOnControlDenialCallback(function () {
        // Called to report the customer has 
		// denied co-browsing session control
		// Add code here to notify agent
    });

    _cbinstance.addOnControlRevokeCallback(function () {
        // Called to report the customer has 
		// revoked co-browsing session control
		// Add code here to notify agent
    });

    _cbinstance.addOnSessionCloseCallback(function (evt) {
        // Called to report the customer has 
		// closed co-browsing session control
		// Add code here to notify agent
    });

    _cbinstance.addOnCustomerJoinCallback(function () {
        // Called to report the customer has 
		// joined co-browsing session control
		// Add code here to notify agent
    });

    _cbinstance.addOnConnectionFailureCallback(function (evt) {
        // Called to report the network connection is 
		// failed
		// Add code here to notify agent
    });

    _cbinstance.addOnConnectionCallback(function (evt) {
        // Called to report the network connection has been 
		// established
		// Add code here to notify agent
    });

    _cbinstance.addOnInActivityTimeOutOccurredCallback(function (message) {
        // Called to report the agent is inactive during 
		// active co-browsing session
		// Add code here to notify agent
    });

    _cbinstance.addOnStopInActivityTimeOutCallback(function (message) {
        // Called to report the agent has become active during 
		// active co-browsing session
		// Add code here to notify agent
    });
```

##### Agent Request Session

```javascript
	var onSuccess = function (data) {
		// Called to report co-browsing session
		// has been created successfully
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in request session
		// Add code here to notify agent
	};	
	
	_cbinstance.requestSession(name, locale,emailId).then(onSuccess, onFailure);
```

##### Agent Request Session Control

```javascript
	var onSuccess = function (data) {
		// Called to report agent has requested
		// control of Co-Browsing Session
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in 
		// request co-browsing session control
		// Add code here to notify agent
	};	
 
	_cbinstance.requestControl().then(onSuccess, onFailure);
```
##### Agent Release Control

```javascript	 
	_cbinstance.releaseControl();
```

#### Customer Website

This describes implementation of Customer Service Co-Browsing features on Customer Website

##### Customer Service Initialization

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

    var _coBrowseAgentClientService = new AvayaCoBrowseClientServices(_cbconfig);
	// To register logger
    _coBrowseAgentClientService.registerLogger(window.console);

	_cbinstance = _coBrowseAgentClientService.createCustomerCobrowse(_cbconfig);
    _cbinstance.start();

    _cbinstance.addOnConnectionResetCallback(function (evt) {
		// Called to report the network connection has been 
		// re-established
		// Add code here to notify customer
    });

    _cbinstance.addOnConnectionFailureCallback(function (evt) {
        // Called to report the network connection is 
		// failed
		// Add code here to notify customer
    });

   _cbinstance.addOnConnectionCallback(function (evt) {
        // Called to report the network connection has been 
		// established
		// Add code here to notify customer
    });

    _cbinstance.addOnSessionCloseCallback(function (evt) {
        // Called to report the agent has 
		// closed co-browsing session
		// Add code here to notify customer
    });

    _cbinstance.addOnControlRequestCallback(function (evt) {
        // Called to report the agent has 
		// requested co-browsing session control
		// Add code here to notify customer
    });

    _cbinstance.addOnControlReleaseCallback(function (evt) {
        // Called to report the agent has 
		// released co-browsing session control
		// Add code here to notify customer
    });

    _cbinstance.addOnfireInactivityCallback(function (msg) {
        // Called to report the customer is inactive during 
		// active co-browsing session
		// Add code here to notify customer
    });

    _cbinstance.addOnStopInactivityTimerCallback(function (msg) {
        // Called to report the customer is active during 
		// active co-browsing session
		// Add code here to notify customer
    });

    _cbinstance.addOnAgentJoinCallback(function (evt) {
        // Called to report the agent has 
		// joined co-browsing session control
		// Add code here to notify customer
    });
```

##### Customer Join Session

```javascript
	var onSuccess = function (data) {
		// Called to report live co-browsing session
		// has been joined successfully
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in join live session
		// Add code here to notify agent
	};	
	
    _cbinstance.joinSession(name, sessionKey).then(onSuccess.bind(this),onFailure);
```

##### Customer Pause Session

```javascript
	var onSuccess = function (data) {
		// Called to report co-browsing
		// session is paused
		// Add code here to notify customer
	};

	var onFailure = function (error) {
		// Called to report failure in 
		// pause co-browsing session
		// Add code here to notify customer
	};	

	_cbinstance.pause().then(onSuccess.bind(this), onFailure);
```

##### Customer Resume Session

```javascript
	var onSuccess = function (data) {
		// Called to report co-browsing
		// session is resumed
		// Add code here to notify customer
	};

	var onFailure = function (error) {
		// Called to report failure in 
		// resume co-browsing session
		// Add code here to notify customer
	};	

	_cbinstance.resume().then(onSuccess.bind(this), onFailure);
```

##### Customer Denies Session Control

```javascript
	var onSuccess = function () {
		// Called to report customer has denied
		// control of Co-Browsing Session
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in 
		// deny co-browsing session control
		// Add code here to notify agent
	};	

    _cbinstance.denyControl().then(onSuccess.bind(this), onFailure);
```

##### Customer Allow Session Control

```javascript
	var onSuccess = function () {
		// Called to report customer has granted
		// control of Co-Browsing Session
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in 
		// grant co-browsing session control
		// Add code here to notify agent
	};	

    _cbinstance.grantControl().then(onSuccess.bind(this), onFailure);
```

##### Customer Logout Session

```javascript
	var onSuccess = function (data) {
		// Called to report agent is
		// logged out successfully
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in ,logout session
		// Add code here to notify agent
	};	
	
	_cbinstance.logoutSession().then(onSuccess, onFailure);
```

### Customer Initiated Co-Browsing session

This section describes 

* <a href="../guide/customer_initialize_sdk.gsp">Initializing the Customer Service</a>
* <a href="../guide/agent_initialize_sdk.gsp">Initializing the Agent Service</a>
* <a href="../guide/customer_request_session.gsp">Request Co-Browsing Session</a>
* <a href="../guide/agent_live_join_session.gsp">Join Co-Browsing Session</a>
* <a href="../guide/customer_pause_session.gsp">Pause Co-Browsing Session</a>
* <a href="../guide/customer_resume_session.gsp">Resume Co-Browsing Session</a>
* <a href="../guide/agent_request_control.gsp">Request Co-Browsing Session Control</a>
* <a href="../guide/customer_deny_control.gsp">Deny Co-Browsing Session Control</a>
* <a href="../guide/customer_deny_control.gsp">Grant Co-Browsing Session Control</a>
* <a href="../guide/customer_revoke_control.gsp">Revoke Co-Browsing Session Control</a>
* <a href="../guide/agent_logout_session.gsp">Logout Co-Browsing Session</a>

![Overview]({{=BpImages}}javascript/sharing/tech/AgentInitiatedSession.png)


#### Customer Website

This describes implementation of Customer Service Co-Browsing features on Customer Website

##### Customer Service Initialization

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

    var _coBrowseAgentClientService = new AvayaCoBrowseClientServices(_cbconfig);
	
	// To register logger
    _coBrowseAgentClientService.registerLogger(window.console);

	_cbinstance = _coBrowseAgentClientService.createCustomerCobrowse(_cbconfig);
    _cbinstance.start();

    _cbinstance.addOnConnectionResetCallback(function (evt) {
		// Called to report the network connection has been 
		// re-established
		// Add code here to notify customer
    });

    _cbinstance.addOnConnectionFailureCallback(function (evt) {
        // Called to report the network connection is 
		// failed
		// Add code here to notify customer
    });

   _cbinstance.addOnConnectionCallback(function (evt) {
        // Called to report the network connection has been 
		// established
		// Add code here to notify customer
    });

    _cbinstance.addOnSessionCloseCallback(function (evt) {
        // Called to report the agent has 
		// closed co-browsing session
		// Add code here to notify customer
    });

    _cbinstance.addOnControlRequestCallback(function (evt) {
        // Called to report the agent has 
		// requested co-browsing session control
		// Add code here to notify customer
    });

    _cbinstance.addOnControlReleaseCallback(function (evt) {
        // Called to report the agent has 
		// released co-browsing session control
		// Add code here to notify customer
    });

    _cbinstance.addOnfireInactivityCallback(function (msg) {
        // Called to report the customer is inactive during 
		// active co-browsing session
		// Add code here to notify customer
    });

    _cbinstance.addOnStopInactivityTimerCallback(function (msg) {
        // Called to report the customer is active during 
		// active co-browsing session
		// Add code here to notify customer
    });

    _cbinstance.addOnAgentJoinCallback(function (evt) {
        // Called to report the agent has 
		// joined co-browsing session control
		// Add code here to notify customer
    });
```

##### Customer Request Session

```javascript
	var onSuccess = function (data) {
		// Called to report co-browsing session
		// has been created successfully
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in request session
		// Add code here to notify agent
	};	
	
	_cbinstance.requestSession(name, locale).then(onSuccess.bind(this), onFailure);
```

##### Customer Pause Session

```javascript
	var onSuccess = function (data) {
		// Called to report co-browsing
		// session is paused
		// Add code here to notify customer
	};

	var onFailure = function (error) {
		// Called to report failure in 
		// pause co-browsing session
		// Add code here to notify customer
	};	

	_cbinstance.pause().then(onSuccess.bind(this), onFailure);
```

##### Customer Resume Session

```javascript
	var onSuccess = function (data) {
		// Called to report co-browsing
		// session is resumed
		// Add code here to notify customer
	};

	var onFailure = function (error) {
		// Called to report failure in 
		// resume co-browsing session
		// Add code here to notify customer
	};	

	_cbinstance.resume().then(onSuccess.bind(this), onFailure);
```

##### Customer Denies Session Control

```javascript
	var onSuccess = function () {
		// Called to report customer has denied
		// control of Co-Browsing Session
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in 
		// deny co-browsing session control
		// Add code here to notify agent
	};	

    _cbinstance.denyControl().then(onSuccess.bind(this), onFailure);
```

##### Customer Allow Session Control

```javascript
	var onSuccess = function () {
		// Called to report customer has granted
		// control of Co-Browsing Session
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in 
		// grant co-browsing session control
		// Add code here to notify agent
	};	

    _cbinstance.grantControl().then(onSuccess.bind(this), onFailure);
```

##### Customer Revoke Control

```javascript
	var onSuccess = function (data) {
		// Called to report customer has revoked
		// control of Co-Browsing Session
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in 
		// request co-browsing session control
		// Add code here to notify agent
	};	
	
    _cbinstance.revokeControl().then(onSuccess.bind(this), onFailure);
```

#### Agent Website

This describes implementation of Agent Service Co-Browsing features on Agent Website

##### Agent Service Initialization

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

    var _coBrowseAgentClientService = new AvayaCoBrowseClientServices(_cbconfig);
	
	// To register logger
    _coBrowseAgentClientService.registerLogger(window.console);

	_cbinstance = _coBrowseAgentClientService.createAgentCobrowse(_cbconfig);
	
	// To set IFrame which renders customer webpage
    _cbinstance.setIFrame(_iframeId);
    _cbinstance.start();

    _cbinstance.addOnPauseCallback(function () {
		// Called to report the customer has 
		// paused co-browsing session
		// Add code here to notify agent
    });
	
    _cbinstance.addOnResumeCallback(function () {
        // Called to report the customer has 
		// resume co-browsing session
		// Add code here to notify agent
    });

    _cbinstance.addOnControlGrantCallback(function () {
        // Called to report the customer has 
		// granted co-browsing session control
		// Add code here to notify agent
    });

    _cbinstance.addOnControlDenialCallback(function () {
        // Called to report the customer has 
		// denied co-browsing session control
		// Add code here to notify agent
    });

    _cbinstance.addOnControlRevokeCallback(function () {
        // Called to report the customer has 
		// revoked co-browsing session control
		// Add code here to notify agent
    });

    _cbinstance.addOnSessionCloseCallback(function (evt) {
        // Called to report the customer has 
		// closed co-browsing session control
		// Add code here to notify agent
    });

    _cbinstance.addOnCustomerJoinCallback(function () {
        // Called to report the customer has 
		// joined co-browsing session control
		// Add code here to notify agent
    });

    _cbinstance.addOnConnectionFailureCallback(function (evt) {
        // Called to report the network connection is 
		// failed
		// Add code here to notify agent
    });

    _cbinstance.addOnConnectionCallback(function (evt) {
        // Called to report the network connection has been 
		// established
		// Add code here to notify agent
    });

    _cbinstance.addOnInActivityTimeOutOccurredCallback(function (message) {
        // Called to report the agent is inactive during 
		// active co-browsing session
		// Add code here to notify agent
    });

    _cbinstance.addOnStopInActivityTimeOutCallback(function (message) {
        // Called to report the agent has become active during 
		// active co-browsing session
		// Add code here to notify agent
    });
```

##### Agent Join Session

```javascript
	var onSuccess = function (data) {
		// Called to report live co-browsing session
		// has been joined successfully
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in join live session
		// Add code here to notify agent
	};	
	
	_cbinstance.joinLiveSession(name, sessionKey).then(onSuccess, onFailure);
```

##### Agent Request Session Control

```javascript
	var onSuccess = function (data) {
		// Called to report agent has requested
		// control of Co-Browsing Session
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in 
		// request co-browsing session control
		// Add code here to notify agent
	};	
 
	_cbinstance.requestControl().then(onSuccess, onFailure);
```
##### Agent Logout Session

```javascript
	var onSuccess = function (data) {
		// Called to report agent is
		// logged out successfully
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in ,logout session
		// Add code here to notify agent
	};	
	
	_cbinstance.logoutSession().then(onSuccess, onFailure);
```