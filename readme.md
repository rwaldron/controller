# The Controller Object


## Description

The `Controller` object is a single object that has named properties, some of which are functions.

The value of the `[[Prototype]]` internal property of the `Controller` object is the standard built-in `Object` prototype object (ES 15.2.4). The value of the `[[Class]]` internal property of the `Controller` object is "*Controller*".

The `Controller` object does not have a `[[Construct]]` internal property; it is not possible to use the `Controller` object as a constructor with the new operator.

The `Controller` object does not have a `[[Call]]` internal property; it is not possible to invoke the `Controller` object as a function.


## Value Properties of the Controller Object


 - ...


## Function Properties of the Controller Object

 - `queryState()` Returns an object descriptor that represents the current state of







# DOM Events

## Current

#### Events

 - buttondown (`MozJoyButtonDown`)
 - buttonup (`MozJoyButtonUp`)
 - axismove (`MozJoyAxisMove`)


## Propose

Implement new `UIEvent` interface: `DeviceEvent`

The DOM `DeviceEvent` represents events that occur as a result of the user interacting with a device (in this case, not a keyboard and not a mouse).

The event object of a `DeviceEvent` should provide a value property named `state` who's value is an object descriptor representing the complete state of the device.

The event object of a `DeviceEvent` should provide a value property named `type` who's value is a string that describes the event that occurred as result of of the user interacting with the device.


#### Events

 - *interact*
 - *connect*
 - *disconnect*




