{{= BackToPackageOverview }}

#Marking During Co-Browsing Session

Using the Sharing Services Package, the Agent can use the marker feature during active Co-Browsing session. 

To enable marker feature, you must complete the following activities.

* Enable Marker

To disable marker feature, you must complete the following activities.

* Disable Marker

To set marker color, you must complete the following activities.

* Set Marker Color

To clear all agent markers on the Co-Browse webpage

* Clear All Agent Markers

To Hide all customer markers on the Co-Browse webpage

* Hide All Customer Markers

To UnHide all customer markers on the Co-Browse webpage

* UnHide All Customer Markers

To Hide all agent markers on the Co-Browse webpage

* Hide All Agent Markers

To UnHide all agent markers on the Co-Browse webpage

* UnHide All Agent Markers
 

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

##Clear All Agent Markers

Call removeAllAgentMarkers() method to clear all the agent markers on the  marked text on the Co-Browse webpage

```javascript
	_cbinstance.removeAllAgentMarkers();
```
Note - Single click on a specific agent marker removes it from the webpage.

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