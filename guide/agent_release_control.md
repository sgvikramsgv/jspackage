{{= BackToPackageOverview }}

#Release Co-Browsing Session Control

Using the Sharing Services Package, the Agent can release a Co-Browsing session control during active Co-Browsing. 

##Release Control

Call releaseControl() method to release Co-Browsing Session Control. Agent will be in readonly mode after releasing Co-Browsing session control. Customer gets notification through callbacks.

```javascript	 
	_cbinstance.releaseControl();
```