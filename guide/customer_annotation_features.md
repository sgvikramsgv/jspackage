{{= BackToPackageOverview }}

#Annotation During Co-Browsing Session

Using the Sharing Services Package, the Customer can start or stop annotation during active Co-Browsing session. 

To start annotation feature, you must complete the following activities.

* Register Start Annotation Callbacks
* Start Annotation

To start annotation using a shape, color and stroke size, you must complete the following activity.

* Register Set Annotation Callbacks
* Set Annotation Shape Information

To stop annotation feature, you must complete the following activities.

* Register Stop Annotation Callbacks
* Stop Annotation

To clear all customer annotations on the Co-Browse webpage

* Clear All Customer Annotations

To Hide all agent annotations on the Co-Browse webpage

* Hide All Agent Annotations

To UnHide all agent annotations on the Co-Browse webpage

* UnHide All Agent Annotations

To Hide all Customer annotations on the Co-Browse webpage

* Hide All Customer Annotations

To UnHide all customer annotations on the Co-Browse webpage

* UnHide All Customer Annotations
 

##Register Start Annotation Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that customer can Annotate on the active Co-Browse webpage. While annotating on the webpage customer is not allowed to update values for the webpage elements. The onFailure callback is called to report a failure that customer cannot Annotate on the active Co-Browse webpage. 

```javascript
	var onSuccess = function () {
		// Called to report success for start Annotation
		// Add custom GUI code for the customer to use the Annotation feature
		//e.g. Display a toolbar which allows customer to select color, shape or stroke size for annotation on webpage
	};

	var onFailure = function (error) {
		// Called to report failure in 
		// Start Annotation feature
		// Add code here to notify customer
	};	
```

##Start Annotation

Call startAnnotation() method to allow customer annotate on the Co-Browse webpage.

```javascript	 
    _cbinstance.startAnnotation().then(onSuccess.bind(this), onFailure);;
```


##Register Set Annotation Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that customer can Annotate on the active Co-Browse webpage using the specified annoation shape information obtained from the {{=C_ServicesCobrowseCommonAnnotationShapeInfo}} object. 
The onFailure callback is called to report a failure that customer cannot Annotate on the active Co-Browse webpage. 

```javascript
    var onSuccess = function () {
        // Called to report success for setting the Annotation object 
    };

    var onFailure = function (error) {
        // Called to report failure for setting the Annotation object 
    };	
```

##Set Annotation Shape Information

Call setAnnotation({{=C_ServicesCobrowseCommonAnnotationShapeInfo}}) method to specify the annotation shape type used for annotating on Co-Browse webpage.
The supported annotation shape types and the respective variables are as follows:

* For Rectangle - AvayaCoBrowseClientServices.Services.Cobrowse.Common.AnnotationShapeType.ANNOTATIONSHAPETYPERECTANGLE
* For Circle - AvayaCoBrowseClientServices.Services.Cobrowse.Common.AnnotationShapeType.ANNOTATIONSHAPETYPECIRCLE
* For FreeHand - AvayaCoBrowseClientServices.Services.Cobrowse.Common.AnnotationShapeType.ANNOTATIONSHAPETYPEFREEHAND

The default annotation shape type is FreeHand

```javascript
    //Create AnnotationInfo object with default values as
    //strokeColor=red, strokeSize=5, annotationShapeType=AvayaCoBrowseClientServices.Services.Cobrowse.Common.AnnotationShapeType.ANNOTATIONSHAPETYPEFREEHAND
    var annotationInfo = new AvayaCoBrowseClientServices.Services.Cobrowse.Common.AnnotationShapeInfo();
    
    //Create AnnotationInfo object with user specified values 
    //Customer annotates on webpage using Rectangle Shape with strokeColor and strokeSize as 'blue' and '11'
    
    var annotationInfo= new AvayaCoBrowseClientServices.Services.Cobrowse.Common.AnnotationShapeInfo('blue','11',AvayaCoBrowseClientServices.Services.Cobrowse.Common.AnnotationShapeType.ANNOTATIONSHAPETYPERECTANGLE);
    
    //Call to setAnnotation method
    _cbinstance.setAnnotation(annotationInfo).then(onSuccess.bind(this), onFailure);	

```

##Register Stop Annotation Callbacks

You must register onSuccess and onFailure callbacks. The onSuccess callback is called to report that customer can no longer annotate on the webpage. The onFailure callback is called to report a failure for the api call. 

```javascript
    var onSuccess = function () {
        //Called to report success for stop Annotation. 
        //Now customer can update the webpage elements
        //Customer is not allowed to annotate on the webpage until an api call is made to start the annotation  
    };

    var onFailure = function (error) {
        // Called to report failure in 
        // Stop Annotation api call
        // Add code here to notify customer
    };	
```

##Stop Annotation

Call stopAnnotation() api to disable the annotation mode.

```javascript	 
    _cbinstance.stopAnnotation().then(onSuccess.bind(this), onFailure);
```

##Clear All Customer Annotations

Call clearAllCustomerAnnotations() method to remove all the customer annotations on the Co-Browse webpage.

```javascript	 
    _cbinstance.clearAllCustomerAnnotations();
```
Note - Single click on a specific annotation removes it from the webpage.

##Hide All Agent Annotations

Call hideAllAgentAnnotations() method to hide all agent annotations on the Co-Browse webpage.

```javascript	 
    _cbinstance.hideAllAgentAnnotations().then(onSuccess.bind(this), onFailure);
```

##UnHide All Agent Annotations

Call unHideAllAgentAnnotations() method to unHide agent annotations on the Co-Browse webpage.

```javascript	 
    _cbinstance.unHideAllAgentAnnotations().then(onSuccess.bind(this), onFailure);
```

##Hide All Customer Annotations

Call hideAllCustomerAnnotations() method to hide all customer annotations on the Co-Browse webpage.

```javascript	 
    _cbinstance.hideAllCustomerAnnotations().then(onSuccess.bind(this), onFailure);
```

##UnHide All Customer Annotations

Call unHideAllCustomerAnnotations() method to unHide customer annotations on the Co-Browse webpage.

```javascript	 
    _cbinstance.unHideAllCustomerAnnotations().then(onSuccess.bind(this), onFailure);
```