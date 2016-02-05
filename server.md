
# Meteor Velocity Jasmine

### Sever Unit

##### Overview

Server Unit tests are for testing individual methods in serverside code...profound, I know. 

We are testing:

* for expected return value
* for propper error handling
* for expected number of calls to that method
* for other methods being called within said method 

It is essential in server unit testing to look at isolated peices of code. Breakdown an essential peice of the app and figure out how to test the most simple peices of it (individual methods). If you can test all the basic functions of that feature, you can have a strong confidence that all of the peices will work in concert. 

We are **not** testing:

* the overall state of the app after the method is called 
* for actuall changes to the app's DB  
* for changes to the DOM

### Setting up Server Unit Tests

##### MeteorStubs

In Meteor Server side tests, we have access to the whole meteor ecosystem and our source code. There is no need to stub out Meteor as a whole (which you do have to do client side).

##### Using Spies

Spies in Jasmine mock methods. They will keep track of whether a method is called, how many times, with what arguments. We can also force spied methods to return a value. This way we can test things in a controlled environment, testing only the behavior of one method at a time. This is the heart of unit testing. You may say, 'Well if we force internal methods to have the values we say they should have, then of course we are going to get what we epect. What are we really testing?'. We want to test every single method in out app with its own unit test(s) even if it seems obvious what it will/should do. As our app grows in size and complexity, these tests will serve as a bench mark. 


There are two ways to use spies - `createSpy()` and `spyOn()`. 

`spyOn()` takes an object as its first argument, and a method on that object as its second. So this means that to use spyOn methods must be part of an object.

`createSpy` will turn a method not attached to an object into a spy.

```coffee

EXAMPLE CODE

```   
As well, we can chain methods onto these spies. Check it out.

```coffee

EAMPLE CODE

```

Also use: .callThrough