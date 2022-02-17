{{= BackToPackageOverview }}

#Join Co-Browsing Session

Using the Sharing Services Package, the Agent can join live Co-Browsing session created by Customer. 

To join a Co-Browsing session, you must complete the following activities.

* Register Join Live Session Callbacks
* Join Live Session 

##Register Join Live Session Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that Agent has joined 
live session successfully.Customer gets notification that agent has joined the session. The onFailure callback is called to report a failure in live join session 

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
```

##Join Live Session

In order to join a Co-Browsing session, you must provide agent name and session key. Session Key is shared by 
Customer during voice call or chat or video. 

```javascript
	_cbinstance.joinLiveSession(name, sessionKey).then(onSuccess, onFailure);
```

