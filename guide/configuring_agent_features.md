{{= BackToPackageOverview }}

#Configuring the Agent Features

Using the Sharing Services Package, you can configure Co-Browsing features for the Agent website. 

##Enable Highlight

Use the enableHighlight() method to enable the Highlight feature. By default the Highlight feature is enabled.

```javascript
	_cbinstance.enableHighlight();
```

##Disable Highlight

Use the disableHighlight() method to disable the Highlight feature.

```javascript
	_cbinstance.disableHighlight();
```

##Enable Element Highlight

Use the enableElementHighlight() method to enable the Highlight element feature. By default the Highlight element feature is enabled.

```javascript
	_cbinstance.enableElementHighlight();
```

##Disable Element Highlight

Use the disableElementHighlight() method to disable the Highlight element feature.

```javascript
	_cbinstance.disableElementHighlight();
```

##Connection Retry Attempts

To set connection retry attempts, you must provide the count. This specifies the number of attempts that the Agent service makes to connect to the Breeze server. The default value is 10. 

```javascript
	_cbinstance.setAgentConnectionRetryAttempts(retryAttempts);
```

##Connection Retry Interval

To set connection retry attempts, you must provide the time in milliseconds. This specifies the interval after which the Agent service attempts to connect to the Breeze server. The default value is 10000. 

```javascript
	_cbinstance.setAgentConnectionRetryInterval(connectionRetryInterval);
```

##Set CSS Path

To set css path, you must provide the css directory path. The default value is css/. 

```javascript
	_cbinstance.setAgentCSSPath(AgentCSSPath);
```

##Set Image Path

To set image path, you must provide the image directory path. The default value is img/. 


```javascript
	_cbinstance.setAgentImagePath(AgentImagePath);
```

##Set IFrame

To render the Customer webpage on IFrame, You must provide IFrameId.

```javascript
	// To set IFrame which renders customer webpage
	_cbinstance.setIFrame(iFrameId);
```

##Set Mouse and Scroll Synchronization Interval

To set the mouse and scroll synchronization interval, you must provide the time in milliseconds. This specifies the interval after which the Agent synchronizes mouse trails and scroll position with the Customer.The default value is 1000. 

```javascript
	_cbinstance.setMouseScrollSyncInterval(mouseScrollSyncInterval);
```

##Update inactivity timeout

To record inactivity timeout activities, you must provide the time in seconds.

```javascript
	_cbinstance.updateIdleTime(_inactiveMessageCounter);
```

##Making Configuration Changes at Runtime

Configuration data is critical for initializing the Client SDK. Services are created and initialized according to their corresponding configuration data during initialization.
After the Client SDK is initialized, if you need to change any configuration options for any services or enable/disable certain services, the Client SDK must be re-initialized with the updated configuration data.Dynamic changes of configuration options are not supported.