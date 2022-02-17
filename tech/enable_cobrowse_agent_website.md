{{= BackToPackageOverview }}

#Enable Co-Browsing on the Agent Website

This article describes ways to enable Co-Browsing solution on Agent website.

## Planning 

Before you begin implementing Co-Browsing for your application, ensure you:

* Add an iframe on the Agent webpage for showing Co-Browsing contents.
* Analysis of website to be cobrowsed with against JS libraries used in Co-Browsing solution against any potential conflict.
* NAMESPACE analysis of the website against Co-Browsing solution's NAMESPACE for any potential conflict
* Optionally, you can disable the inline scripts on agent side or restrict the execution of javascripts from certain domains. To do this, you can use the meta tag of the content security policy and add the information under the head section of the web page where the agent iframe is added.
```javascript
<head>
<meta http-equiv='Content-Security-Policy' content='script-src self;'>
</head>
```

## Files required to enable Co-Browsing on Agent website

The following table lists the files that are required for enabling Co-Browsing on the Agent website.
The table also provides information about the location and purpose of each file

<p class="av-note"><span>Note:</span>You must include all JavaScript and css files on the Agent website.</p>

| File Name                          | File Path                                                               | Purpose                                                                                                                                           | Comments                                                                                                                                                            |
|------------------------------------|-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AvayaCoBrowseClientServices.min.js | sdk\AvayaCoBrowseClientServices.min.js                                  | Contains all the API interfaces and implementation.                                                                                               | You cannot change anything in this file. It violates the license agreement.                                                                                         |
| jquery_path.js                     | sdk\agent\lib                                                           | Used for manipulation of html element path. This file is consumed by Co-browsing Customer SDK.                                                    | This library is Avaya JavaScript library.Do not change any information in this file.                                                                                |
| Base64.js                          | sdk\common\lib\Base64.js                                                | Used to encrypt and decrypt the html content.                                                                                                     | This is a third party library.                                                                                                                                      |
| jquery.min.js                      | sdk\common\lib\jquery.min.js                                            | This is used for Dom manipulation, CSS manipulation, Html event methods, Ajax calls, and other utilities, such as traversing, adding css effects. | This is a third party library.                                                                                                                                      |
| sock.js                            | sdk\common\lib\sock.js                                                  | Used for transferring data between server and Customer webpages through long polling.                                                             | This is a third party library.                                                                                                                                      |
| agent.css                          | sdk\customer\css\agent.css                                              | The css file consumed by Co-Browsing Agent Service.                                                                                               | Do not change any information in this file.                                                                                                                         |
| pointer.png                        | sdk\customer\img\pointer.png                                            | Used for displaying the mask symbol when the Agent does not have the mouse control and movement of mouse is controlled by the Customer.        | Create an img folder in the directory containing the css folder and then copy this file in the img folder.                                                          |

#### List of 3rd party libraries

| 3rd Party javascript library | Purpose                                                                                                                                                                                                                                                                                                       | Version and information                                                                                                                                                                                                                                                                  |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| sock.js                      | It contains the implementation of sockjs-client.SockJS is a browser JavaScript library that provides a WebSocket-like object. SockJS gives you a coherent, cross-browser, Javascript API which creates a low latency, full duplex, cross-domain communication channel between the browser and the web server. | /* sockjs-client v1.1.1 | http://sockjs.org | MIT license */                                                                                                                                                                                                                             |
| jquery.min.js                | Jquery library is used for Dom manipulation, CSS manipulation, Html event methods, Ajax calls, and other utilities, such as traversing, adding css effects.                                                                                                                                                   | /*! jQuery v1.11.0 | (c) 2005, 2014 jQuery Foundation, Inc. | jquery.org/license */                                                                                                                                                                                                      |
| Base64.js                    | Used to encrypt and decrypt the html content.                                                                                                                                                                                                                                                                 | /* webtoolkit.base64.min.js | http://www.webtoolkit.info/* http://www.webtoolkit.info/javascript_base64.html#.WBHC1yh94dU/                                                                                                                                                               |

## Supported Events

When the agent is in control, co-browsing supports a set of events on html elements for updating contents. The list of events that are supported are:-
 
| Events                        | Html Element                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|--------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| click                       | a, button, input type button, input type submit, checkbox, radio, label, span, li                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
|mouseup | node type text 
|change | select, input type text
|blur | input type text
|focus | input type text
|keypress | input type text, input type radio
|hover | For defined psuedo class on elements
|keyup | input type text, textarea
|scroll | texarea, div
|focusin | a, input, textarea, select, option,optgroup, button, fieldset, legend, img, area, map, nav > li, nav > li> div
|mouseenter | a, input, textarea, select, option,optgroup, button, fieldset, legend, img, area, map, nav > li, nav > li> div
|mouseleave | a, input, textarea, select, option,optgroup, button, fieldset, legend, img, area, map, nav > li, nav > li> div

#### What to do next...

The following is a recommended list of articles to get you started on Customer Website:

* <a href="../tech/develop_cobrowse_app.gsp">Developing Co-Browsing Websites</a>
* <a href="../tech/debugging_tip.gsp">Debugging Tips</a>
