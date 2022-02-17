{{= BackToPackageOverview }}

#Co-Browsing Session Information

Using the Sharing Services Package, you can easily get the Co-Browsing Session information.

The method to retrieve the Co-Browsing Session information is obtained from the {{=C_BaseCobrowseSessionInfo}} object.

##Retrieving Co-Browsing Session information

To get the the Customer name, use the getCustomerName() function.

```javascript
String customerName = _cbinstance.getCustomerData().getCustomerName();
```

To get the control state, use the getAgentControlState() function.

```javascript
String controlState = _cbinstance.getCustomerData().getAgentControlState();
```

To get the Customer authcode, use the getCustomerAuthCode() function.

```javascript
String customerAuthCode = _cbinstance.getCustomerData().getCustomerAuthCode();
```

To get the cobrowse state, use the getCobrowseState() function.

```javascript
String cobrowseState = _cbinstance.getCustomerData().getCobrowseState();
```

To get the reason when a Customer disconnects the Co-Browsing session, use the getCustomerReasonForDisconnect() function.

```javascript
String customerReasonForDisconnect = _cbinstance.getCustomerData().getCustomerReasonForDisconnect();
```

To get the passphrase, use the getPassPhrase() function.

```javascript
String passphrase = _cbinstance.getCustomerData().getPassPhrase()
```

To get the complete Co-Browsing session data, use the getCustomerData() function. This function returns the {{=C_BaseCobrowseSessionInfo}} object.

```javascript
AvayaCoBrowseClientServices.Base.CobrowseSessionInfo cobrowseSessionInfo = _cbinstance.getCustomerData();
```