{{= BackToPackageOverview }}

#Request Co-Browsing Session Control

Using the Sharing Services Package, the Agent can request Co-Browsing session control during active Co-Browsing. 

To request Co-Browsing session control, you must complete the following activities.

* Register Request Co-Browsing Session Control Callbacks
* Request Control 

##Register Request Co-Browsing Session Control Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that the Agent has requested 
control of Co-Browsing Session.The onFailure callback is called to report a failure in request co-browsing session control. 

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
```

##Request Control

Call requestControl() method to request Co-Browsing Session Control. Customer gets notification to grant or deny Co-Browsing Session Control.

```javascript	 
	_cbinstance.requestControl().then(onSuccess, onFailure);
```