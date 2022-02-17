{{= BackToPackageOverview }}

#Marking During Co-Browsing Session

Using the Sharing Services Package, the Customer can use the marker feature during active Co-Browsing session. 

To enable marker feature, you must complete the following activities.

* Enable Marker

To disable marker feature, you must complete the following activities.

* Disable Marker

To set marker color, you must complete the following activities.

* Set Marker Color

To clear all customer markers on the Co-Browse webpage

* Clear All Customer Markers

To Hide all agent markers on the Co-Browse webpage

* Hide All Agent Markers

To UnHide all agent markers on the Co-Browse webpage

* UnHide All Agent Markers

To Hide all customer markers on the Co-Browse webpage

* Hide All Customer Markers

To UnHide all customer markers on the Co-Browse webpage

* UnHide All Customer Markers
 

##Enable Marker

Call the enableMarker() method to enable the marker feature. By default the Marker feature is disabled.

```javascript
	_cbinstance.enableMarker();
```


##Disable Marker

Call the disableMarker() method to disable the Marker feature.

```javascript
	_cbinstance.disableMarker();
```

##Set Marker Color

To set color of marked text. The default value is yellow.

```javascript
	_cbinstance.setMarkerColor();
```

##Clear All Customer Markers

Call clearAllMarkers() method to clear all the customer markers on the  marked text on the Co-Browse webpage

```javascript
	_cbinstance.clearAllMarkers();
```
Note - Single click on a specific customer marker removes it from the webpage.

##Hide All Agent Markers

Call hideAllAgentMarkers() method to hide all agent markers on the Co-Browse webpage.

```javascript	 
    _cbinstance.hideAllAgentMarkers();
```

##unHide All Agent Markers

Call unHideAllAgentMarkers() method to unhide all agent markers on the Co-Browse webpage.

```javascript	 
    _cbinstance.unHideAllAgentMarkers();
```

##Hide All Customer Markers

Call hideAllCustomerMarkers() method to hide all customer markers on the Co-Browse webpage.

```javascript	 
    _cbinstance.hideAllCustomerMarkers();
```

##unHide All Customer Markers

Call unHideAllCustomerMarkers() method to unhide all customer markers on the Co-Browse webpage.

```javascript	 
    _cbinstance.unHideAllCustomerMarkers();
```