# Applying Router Configuration for a Full-Screen Application

*Source: https://learning.sap.com/courses/advanced-sapui5-development/implementing-router-configuration_a90df07d-7729-4716-a776-c0aa6ac16847*

Objective
After completing this lesson, you will be able to apply router configuration for a full-screen application.
## Implementing the Routing for a Full-screen Application
### Routing and Navigation
As discussed, the SAPUI5 allows you to build single-page apps where the navigation is done by changing the hash. In this lesson, we will learn how to configure and implement the navigation for a full-screen application.
![An application displaying a list of flights.](../images/32831df97fa5d0f9.png)
As you have learned, a route is used to notify your application that the hash has changed to a certain value. The pattern of the route is matched against the hash. If the pattern matches, the route provides the data passed over the hash to a defined handler.
### Root View Configuration
In the manifest.json file, in the "sap.ui5" section, there should be a "rootView" section defining the entry point of the application. In most cases, the _App_ view.
The id of the _app_ control is also provided.
![A sample manifest.json file showing the rootView configuration.](../images/f1ed48826a5c5c29.png)
### URL Patterns for Routes
Remember, whenever a hash is added to a URL, the router checks whether there is a route with a matching pattern. The first matching route is taken and the corresponding target view is called. The data provided with the hash are passed on to the target.
The pattern parameter of a route defines the string that is matched against the hash.
Let's review in details the different kinds of patterns:
  * Hardcoded parts
  * Mandatory parameters
  * Optional parameters
  * Mandatory query parameters
  * Optional query parameters

#### URL Patterns for Routes
| Pattern type  | Example  |   |
| --- | --- | --- |
| hardcoded parts  | "carrier/settings"  |  This pattern will only match if the hash of the browser is carrier/settings. No arguments will be passed to the events of the Route.  |
| mandatory parameters  | "carrier/{carrierid}"  |  {carrierid} is a mandatory parameter. For example, the following hashes would match: carrier/AA. The matched event of the Route will get AA passed as carrierid in its arguments. The hash carrier/ will not match.  |
| optional parameters  | "carrier/{carrierid}/showtab/:tabid:"  |  :tabid: is an optional parameter For example, the following hashes would match: carrier/AA/bookings  |
| mandatory query parameters  | "carrier{?query}"  |  {?query} allows you to pass queries with any parameters For example, the following hashes would match: carrier?first=value1 carrier?first=value1&second=value2  |
| optional query parameters  | "carrier/{carrierid}/flights:?query:"  |  :?query: is an optional query parameter. For example, the following hashes would match: carrier/AA/flights?from=New York carrier/AA/flights  |
### Routing applied to a Full-screen Application
In this video lets look at routing in a full screen application.
## Explore the routing configuration of a Full-screen Application
### Business Example
In the following exercise, you will explore the routing configuration of a Full-screen Application with SAPUI5.
### Prerequisites
You should have completed the previous exercise to import the full screen application.
### Steps
  1. Look at the routing configuration and check everything is in place for a full-screen application navigation.
What is the root View?
Look at the controlAggregation, controlId and clearControlAggregation properties.
How many targets? How many routes? Why?
What is the pattern to open the Flights view?
    1. Open the manifest.json file.
    2. Look for the rootView section.
The rootView is the _App_ view.
    3. Look for the routing section.
    4. Check the config section.
The controlAggregation is pages, the controlID is App and the clearControlAggregation is set to false.
    5. Check the routes and targets section.
There are three targets (overview, flights and notFound) and two routes (for overview and flights). The notFound target is used in the config section, as a bypass.
    6. Note the route pattern to open the _Flights_ view.
The pattern to open the Flights view is: carriers/{carrid}
  2. Preview the application.
What does happen if you try to enter a flights view pattern manually? (for example by adding **& /carriers/AA** at the end of the current URL).
What does happen if you enter a wrong pattern? (for example **& /carrier** at the end of the default URL).
    1. Right-click on the webapp folder and choose _Preview Application_.
    2. Select _start local..._
A list of carriers should be displayed.
    3. Change the URL to enter a valid pattern, for example, add **& /carriers/AA**.
The _Flights_ view displays but with no data. No binding has been set yet with the data service.
    4. Change the URL to enter a wrong pattern, for example, change to **& /carrier/AA**.
The _NotFound_ view displays. If you choose the _Go Back_ button, you return to the _Flights_ view.
