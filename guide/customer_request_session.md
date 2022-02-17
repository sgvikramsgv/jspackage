{{= BackToPackageOverview }}

#Request Co-Browsing Session

Using the Sharing Services Package, the Customer can request Co-Browsing session.

To request Co-Browsing session, you must complete the following activities.

* Register Request Session Callbacks
* Request Session 

##Register Request Session Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that Co-Browsing 
session is created successfully. The onFailure callback is called to report a failure in request session.

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

To request a Co-Browsing session, you must provide customer name,locale, and Email. Email is optional.

```javascript
    _cbinstance.requestSession(name, locale).then(onSuccess.bind(this), onFailure);
```