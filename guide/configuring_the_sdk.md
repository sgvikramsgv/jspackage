{{= BackToPackageOverview }}

#Configuring the SDK

Configuration of the Sharing Services Package is defined by using a CoBrowseConfiguration Configuration object. This approach provides flexibility to configure services within a package as required.

##Co-Browsing Configuration

The {{=C_ConfigCoBrowseConfiguration}} class is the most fundamental configuration object for the package. This class is used to describe the Breeze server properties such as host name, port, and security policy. Additional parameters that are accessed through this class include flag to enable Co-Browse and maximum connection retry with Breeze Server.

##Making Configuration Changes at Runtime

Configuration data is critical for initializing the Client SDK. Services are created and initialized according to their corresponding configuration data during initialization.
After the Client SDK is initialized, if you need to change any configuration options for any services or enable/disable certain services, the Client SDK must be re-initialized with the updated configuration data.Dynamic changes of configuration options are not supported.
