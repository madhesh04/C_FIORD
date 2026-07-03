# Quiz

*Source: https://learning.sap.com/courses/developing-uis-with-sapui5-1/routing-and-navigation*

It's time to put what you've learned to the test, get 5 right to pass this unit.
1.
### You have created a Back button on a view and call the getPreviousHash method of the sap.ui.core.routing.History instance in the implementation of the attached event handler. What value does this method return if there has been no navigation in the application yet?
Choose the correct answer.
"" (empty string)
null
undefined
The pattern from the routing configuration that was assigned to the root view of the component.
2.
### You have specified "detail/{customerId}" in the routing configuration as the value for the pattern property of a route. Which of the following URL hashes match this pattern of the route and therefore result in the patternMatched event being fired?
There are four correct answers.
detail
detail/
detail/456
detail/(00505604-4e85-1edd-818f-21e64b9cd2cf)
detail/abc
/detail/456
detail/456/Orders
3.
### In the application descriptor manifest.json the routing configuration can be found in the routing property of the sap.ui5 namespace. What are the sections that make up this routing configuration?
There are three correct answers.
router
targets
config
hashes
routes
4.
### The router provides a method to navigate to a specific route. What is the name of this method?
Choose the correct answer.
display
goTo
navTo
setRoute
5.
### In the routing configuration, one or more targets can be specified to be displayed if no route of the router matches after changing the hash. What is the name of the property used to specify the corresponding targets?
Choose the correct answer.
bypassed
invalidHash
defaultTarget
noMatch
6.
### The component controller Component.js has a method called init in which initializations necessary for the component are implemented. Which of the following method calls must be added to this init method so that the current URL hash is evaluated and the corresponding views are automatically displayed?
Choose the correct answer.
this.getRouter().initialize();
this.getRouter().setup();
this.getRouter().init();
this.getRouter().registerRoutes();
Submit answers[Go to Course](https://learning.sap.com/courses/developing-uis-with-sapui5-1)
