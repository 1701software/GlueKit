GlueKit for Xojo 2015 r2.1
-------------------------

GlueKit was written by 1701 Software (http://www.1701software.com) in order to support cross platform code in Xojo. Currently Xojo is developing the "new framework" which primarily focuses on the iOS platform. The goal is to eventually bring those classes to the desktop/web platforms. However until they do so 100% it is difficult to write one set of business logic to be shared between platforms.

For instance let's say you want to write a class that interacts with a web service. You might subclass the Xojo.Net.HTTPSocket in iOS and utilize its events and methods. This allows you to just interact with that one class without having to integrate the web service code into the presentation layer of your app. The subclass you developed will not work on a desktop or web project because the Xojo.Net.HTTPSocket class is not available. [5/14/2015: Xojo.Net.HTTPSocket has been added in Xojo 2015r2. This example still illustrates the purpose of GlueKit and applicable to GlueKitTCPSocket just the same.]

However if you use GlueKit and subclass from GlueKitHTTPSocket then you get the best of both worlds. GlueKit automatically uses the best framework depending on the situation. GlueKit is a 99% code compatible drop-in replacement for the Xojo new framework. When Xojo does release Xojo.Net.HTTPSocket for desktop you can just change the super class of your web service subclass to Xojo.Net.HTTPSocket and everything should work. We do this be mimicking the Xojo.Net.HTTPSocket methods/properties/events making it a drop-in replacement.

Classes available, purpose, and planned obsolescence:

GlueKitTCPSocket
- Xojo.Net.TCPSocket is not currently available on all desktop platforms.
- Drop in replacement for Xojo.Net.TCPSocket. On desktop uses the TCPSocket class.
- Will be removed once Xojo.Net.TCPSocket is available on the desktop.

GlueKitEasyTCPSocketClient
- This is the Xojo EacyTCPSocketClient source modified to use GlueKitTCPSocket. 
- This provides the ability to subclass the GlueKitEasyTCPSocketClient and use it across all platforms.
- Will be removed once Xojo.Net.TCPSocket is available on the desktop.
- Alternatively can be removed if the EasyTCPSocket comes to iOS and desktop natively. This does not seem likely as Xojo chose to release the source code for the EasyTCPSocketClient as opposed to build it into iOS.

GlueKit_Extensions
- This module provides numerous extensions and methods to assist in development for various new framework shortcomings.
- EncodeBase64/DecodeBase64 provided by Kim Tekinay. See: https://forum.xojo.com/18743-encode-decodebase64-in-ios/p1#p157101 
- EncodeHex extends the Text type.

We do plan to add more classes as we need them for our own projects. We will happily accept pull requests. Please respect the spirit of GlueKit to strictly be a set of extensions for new framework shortcomings. Replacements for new framework classes should be a drop-in replacement.

The goal here is to make GlueKit easily replaceable with Xojo new framework equivalents once available. GlueKit SHOULD get smaller over time.

Please check out our blog at http://dev.1701software.com

UPDATES:
--------

May 15th, 2015: 
 - Removed GlueKitInvalidJSONException as Xojo.Data.InvalidJSONException was introduced in 2015r2.
 - Removed GlueKitHTTPSocket as Xojo.Net.HTTPSocket was introduced in 2015r2.
 - Removed GlueKitFolderItem as Xojo.IO.FolderItem was introduced in 2015r2.
 - Removed GlueKitSpecialFolder as Xojo.IO.SpecialFolder was introduced in 2015r2.
 - Removed GlueKit_Extensions_Mobile as it does not fit the spirit of GlueKit by adding features.
 - Removed .ParseJSON() method from GlueKit_Extensions. Xojo now supports Xojo.Data.ParseJSON() on Desktop.
 - Removed ToText() and ToDouble() Auto extensions. No longer needed because Xojo Auto handling is better on Desktop.

April 4th, 2015: 
 - Removed GlueKitTimer as Xojo.Core.Timer was introduced in 2015r1.
