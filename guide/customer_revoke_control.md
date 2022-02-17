{{= BackToPackageOverview }}

#Revoke Co-Browsing Session Control

Using the Sharing Services Package, the Customer can revoke a Co-Browsing session control during active Co-Browsing. 

To revoke a Co-Browsing session control, you must complete the following activities.

* Register Revoke Co-Browsing Session Control Callbacks
* Revoke Control 

##Register Revoke Co-Browsing Session Control Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that the Customer has revoked 
control of a Co-Browsing Session.The onFailure callback is called to report a failure in revoke Co-Browsing session control. 

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
```

##Revoke Control

Call revokeControl() method to revoke Co-Browsing Session Control.Agent gets notification that the Customer has revoked Co-Browsing Session Control.

```javascript	 
    _cbinstance.revokeControl().then(onSuccess.bind(this), onFailure);
```