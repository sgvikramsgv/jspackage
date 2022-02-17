{{= BackToPackageOverview }}

#Grant Co-Browsing Session Control

Using the Sharing Services Package, the Customer can grant Co-Browsing session control during active Co-Browsing. 

To grant Co-Browsing session control, you must complete the following activities.

* Register Grant Co-Browsing Session Control Callbacks
* Grant Control 

##Register Grant Co-Browsing Session Control Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that the Customer has gratned 
Co-Browsing Session control. The onFailure callback is called to report a failure in grant Co-Browsing session control. 

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
```

##Grant Control

Call grantControl() method to grant Co-Browsing Session Control. Agent gets notification that Customer has granted
Co-Browsing Session Control.

```javascript	 
    _cbinstance.grantControl().then(onSuccess.bind(this), onFailure);
```