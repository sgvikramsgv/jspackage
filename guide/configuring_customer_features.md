{{= BackToPackageOverview }}

#Configuring the Customer Features

Using the Avaya Client SDK, you can configure Co-Browsing features for Customer website. 

## Mask WebPage Fields

You must analyze and find out the fields which need to keep hidden from the Agent. You must apply CSS class to mask webpage fields. 
After CSS class is applied, contents of the fields are not be visible to the Agent.

* Mask button and checkbox.

Add a css style avcobrowse-block in the style. 

```html
<input type="checkbox" name="mkt_message_option" class="avcobrowse-block" value="on" checked="checked" id="pers_email_info"/>
```

* Mask textfields.

Add a css style avcobrowse-mask in the element style. 

```html
<input type="text" name="ssn" placeholder="Social Security Number" class="avcobrowse-mask"/>
```

* Mask common elements like link, text

Add a css style avcobrowse-hide in the element style. 

```html
<li class="avcobrowse-hide"><a href="../CoBrowseOLHCustomer/index.html" target="_blank">Online Help</a></li>
```

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

##Set Highlight Color

To set color of highlighted text. The default value is yellow.

```javascript
	_cbinstance.setHighlightColor();
```

##Support Psuedo Elements And Classes

To add support for Psuedo elements and classes in Cobrowsing.

```javascript
	_cbinstance.setCSSHoverFile({"css": "one.css"});
	//Set the CSS file name containing hover e.g
	//For one CSS file {"css": "one.css"}
	//For multiple CSS file {"css": "one.css, two.css, three.css"}
	//For parsing all the CSS file {"css": ""}
```

##Agent View Synchronization Interval

To set Agent view synchronization interval, you must provide time in milliseconds. 
This specifies the interval after which Customer web page synchronizes with the Agent if there are any changes in Customer webpage. The default value is 500. 

```javascript
	_cbinstance.setAgentViewSyncInterval(agentViewSyncInterval);
```

##Connection Retry Interval

To set connection retry attempts, you must provide time in milliseconds. This specifies the interval after which Customer service attempts to connect with Breeze server. The default value is 10000. 

```javascript
	_cbinstance.setCustomerConnectionRetryInterval(connectionRetryInterval);
```

##Set Mouse and Scroll Synchronization Interval

To set mouse and scroll synchronization interval, you must provide time in milliseconds. This specifies the interval after which the Customer synchronizes mouse trails and scroll position with the Agent. The default value is 1000.

```javascript
	_cbinstance.setMouseScrollSyncInterval(mouseScrollSyncInterval);
```

##Remove Fields to Synchronize with Agent

You can restrict HTML elements which you do not want to synchronize with the Agent webpage. You must provide ID of the DOM element.

```javascript
	_cbinstance.addElementIDToRemove("cbeToolbar");
```

##Update inactivity timeout

To record inactivity timeout activities, you must provide time in seconds.

```javascript
	_cbinstance.updateIdleTime(_inactiveMessageCounter);
```

##Making Configuration Changes at Runtime

Configuration data is critical for initializing the Client SDK. Services are created and initialized according to their corresponding configuration data during initialization.
After the Client SDK is initialized, if you need to change any configuration options for any services or enable/disable certain services, the Client SDK must be re-initialized with the updated configuration data.Dynamic changes of configuration options are not supported.