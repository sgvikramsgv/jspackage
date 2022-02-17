{{= BackToPackageOverview }}

#Pause Co-Browsing Session

Using the Sharing Services Package, the Customer can pause a Co-Browsing session during active Co-Browsing. 

To pause a Co-Browsing session, you must complete the following activities.

* Register Pause Co-Browsing Session Callbacks
* Pause Co-Browsing Session 

##Register Pause Co-Browsing Session Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that Co-Browsing session is paused.
The onFailure callback is called to report a failure in pause Co-Browsing session. 

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
```

##Pause Co-Browsing Session

Call pause() method to pause Co-Browsing Session.Agent gets notification that Co-Browsing session is paused.

```javascript	 
	_cbinstance.pause().then(onSuccess.bind(this), onFailure);
```