{{= BackToPackageOverview }}

#Resume Co-Browsing Session

Using the Sharing Services Package, the Customer can resume Co-Browsing session during active Co-Browsing. 

To resume Co-Browsing session, you must complete the following activities.

* Register Resume Co-Browsing Session Callbacks
* Resume Co-Browsing Session 

##Register Resume Co-Browsing Session Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that Co-Browsing session is resumed.The onFailure callback is called to report a failure in resume Co-Browsing session. 

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
```

##Resume Co-Browsing Session

Call resume() method to resume Co-Browsing Session.Agent gets notification that the Customer has resumed the session.

```javascript	 
	_cbinstance.resume().then(onSuccess.bind(this), onFailure);
```