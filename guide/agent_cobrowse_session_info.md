{{= BackToPackageOverview }}

#Co-Browsing Session Information

Using the Sharing Services Package, you can easily get the Co-Browsing Session information.

The method to retrieve the Co-Browsing Session information is obtained from the {{=C_BaseCobrowseSessionInfo}} object.

##Retrieving Co-Browsing Session information

To get the Agent name, use the getAgentName() function.

```javascript
String agentName = _cbinstance.getAgentData().getAgentName();
```

To get the control state, use the getAgentControlState() function.

```javascript
String agentControlState = _cbinstance.getAgentData().getAgentControlState();
```

To get the Agent authcode, use the getAgentAuthCode() function.

```javascript
String agentAuthCode = _cbinstance.getAgentData().getAgentAuthCode();
```

To get the Co-Browsing session state, use the getCobrowseState() function.

```javascript
String cobrowseState = _cbinstance.getAgentData().getCobrowseState();
```

To get the reason when a Customer disconnects the Co-Browsing session, use the getCustomerReasonForDisconnect() function.

```javascript
String customerReasonForDisconnect = _cbinstance.getAgentData().getCustomerReasonForDisconnect();
```

To get the passphrase, use the getPassPhrase() function.

```javascript
String passphrase = _cbinstance.getAgentData().getPassPhrase();
```

To get the complete Co-Browsing session data, use the getAgentData() function. This function returns the {{=C_BaseCobrowseSessionInfo}} object.

```javascript
AvayaCoBrowseClientServices.Base.CobrowseSessionInfo cobrowseSessionInfo = _cbinstance.getAgentData();
```