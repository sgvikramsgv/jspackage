{{= BackToPackageOverview }}

#Deny Co-Browsing Session Control

Using the Sharing Services Package, the Customer can deny Co-Browsing session control during active Co-Browsing. 

To deny Co-Browsing session control, you must complete the following activities.

* Register Deny Co-Browsing Session Control Callbacks
* Deny Control 

##Register Deny Co-Browsing Session Control Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that Customer has denied 
Co-Browsing Session control. The onFailure callback is called to report a failure in deny Co-Browsing session control. 

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
```

##Deny Control

Call denyControl() method to deny Co-Browsing Session Control. Agent gets notification that the Customer has denied
Co-Browsing Session Control.

```javascript	 
    _cbinstance.denyControl().then(onSuccess.bind(this), onFailure);
```