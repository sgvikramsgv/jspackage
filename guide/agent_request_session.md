{{= BackToPackageOverview }}

#Request Co-Browsing Session

Using the Sharing Services Package, the Agent can request a Co-Browsing session.

To request a Co-Browsing session, you must complete the following activities:

* Register Request Session Callbacks
* Request Session 
* Register Join Session Callbacks
* Join Session 

##Register Request Session Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that the Co-Browsing 
session is created successfully. The onFailure callback is called to report a failure in the request session.

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
```

##Request Session

To request a Co-Browsing session, you must provide agent name, locale, and Email. Email is optional.

```javascript
	_cbinstance.requestSession(name, locale,emailId).then(onSuccess, onFailure);
```

##Register Join Session Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report agent has joined  the
session successfully. The onFailure callback is called to report a failure in the join session. 

```javascript
	var onSuccess = function (data) {
		// Called to report co-browsing session
		// has been joined successfully
		// Add code here to notify agent 
	};

	var onFailure = function (error) {
		// Called to report failure in join session
		// Add code here to notify agent
	};	
```

##Join Session

To join Co-Browsing session, you must provide acstoken. You can get acstoken using the getAgentAuthCode() method. For more information,
 see <a href="../guide/agent_cobrowse_session_info.gsp">Co-Browsing Session Information</a>.

```javascript
	 String acstoken = _cbinstance.getAgentData().getAgentAuthCode();
	_cbinstance.joinSession(acstoken).then(onSuccess, onFailure);
```