{{= BackToPackageOverview }}

#Debugging Tips

This chapter provides information about Co-Browsing Services implementation debugging. 

## Client side debugging

* Load the newly co-browsing configured page in your browser
* Open the developer tool by pressing F12
* Navigate to console tab and see if there any issues
* Web developer would have sufficient information about the issues and can use the developer tools analyze and fix the problem

## Cross-Origin XHR

* You do not need to implement CORS while developing the co-browse application.CORS is already provided by Breeze platform.
You can have customised deployment strategy (such as usage of reverse proxy in the DMZ) with 1 more layer of CORS implementation.

## Message Transport

* Co-browsing solution uses a 3rd party library for adding a COMET support in the application to stay connected. 
In current version, an http request is used to communicate messages on the async bus. 

## Points to remember

* It should be noted that the renderer (your browser) runs on rules set by html, css and js. If your page has custom elements which use js, css and html combination to work (apart from default html UI elements) you need to provision support these css, js and html in your Agent implementation.
* For security reasons the Co-Browsing application removes all the JavaScript elements in your page before it is shunted to the Agent. 
In cases where the Agent is in control, even the execution of these JS files is blocked.

