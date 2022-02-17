{{= BackToPackageOverview }}

#Logout Co-Browsing Session

Using the Sharing Services Package, the Agent can logout Co-Browsing session. 

To logout Co-Browsing session, you must complete the following activities.

* Register Logout Session Callbacks
* Logout Session 

##Register Logout Session Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that the Agent is logged out   successfully. Customer gets notification that Agent is logged out. The onFailure callback is called to report a failure in logout session 

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
```

##Logout Session

To logout a Co-Browsing session, you can provide logout reason (Optional).

```javascript
	_cbinstance.logoutSession().then(onSuccess, onFailure);
```

##Custom example of Logout Session

 - Logout when customer refreshes the page or closes the window.
 
```javascript
$(window).bind("beforeunload", function() {
var reason = "Customer closed window.";
var onSuccess = function ()
{ console.log("success"); }
;
var onFailure = function (error)
{ console.log("fail"); }
;
_cbinstance.logoutSession(reason).then(onSuccess.bind(this), onFailure);
})
```