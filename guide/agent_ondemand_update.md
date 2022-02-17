{{= BackToPackageOverview }}

#OnDemand Update

Using the Sharing Services Package, the Agent can render the Customer webpage on demand.

##OnDemand Update

Call onDemandUpdate() method to get latest customer webpage during active Co-Browsing. This fuctiontionality is useful when the Agent and the Customer webpage are not in sync. 

```javascript	 
	_cbinstance.onDemandUpdate();
```