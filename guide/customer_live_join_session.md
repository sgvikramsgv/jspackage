{{= BackToPackageOverview }}

#Join Co-Browsing Session

Using the Sharing Services Package, the Customer can join live Co-Browsing session created by customer. 

To join Co-Browsing session, you must complete the following activities.

* Register Join Live Session Callbacks
* Join Live Session 

##Register Join Live Session Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that the Customer is joined live session successfully.
Agent gets notification that the Customer is joined the session. The onFailure callback is called to report a failure in live join session 

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

To join Co-Browsing session, you must provide customer name, and Session Key. Agent shares session key with the Customer during voice call or chat or video. 

```javascript
    _cbinstance.joinSession(name, sessionKey).then(onSuccess.bind(this),onFailure);
```

